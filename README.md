# hello-world
Ideas and musings. 

First microproject and reason for being here:

Ansible ec2.py does not create a group "windows" which is a standard requirement for anyone dealing with mixed platforms. Nor is it particularly easy to create this group in Ansible using tag_platform_windows (ok it's probably trivial for an Ansible guru but I am not one of those). So I propose to build the windows group by extending ec2.py. Specifically I propose to create a group for each value of tag_platform. Currently the only supported values I'm aware of are 'windows' and (null), (null) implying some flavour of unix. I will probably avoid creating by default a group called "windows" as this may cause unexpected behaviour for users who already have a group of this name (it is kind of a "by convention" name so semi-reserved). However they will easily able to populate or repopulate this group "windows" from the newly created group "tag_platform_windows". As a non-default option I may also enable creating the group "windows" directly. For the "null" group I will create that as "tag_platform_default". The code will handle the future case where EC2 adds more variants to the "platform" attribute. 

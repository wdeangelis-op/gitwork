#Gitwork: A simple git workflow tool
Basically, I was having trouble remembering to always update from origin before branching from dev. This took makes life a tiny bit simpler by combining our basic git workflow into two commands.

###Examples
####Basic Use
`gitwork ONTRA-300`
This is basically an alias for the following commands:
```sh
git checkout dev
git pull origin dev
git checkout -b ONTRA-300
```

####Additional Arguments:
`gitwork ONTRA-300 master alternate_origin`
Will do the following:
```sh
git checkout master
git pull alternate_origin dev
git checkout -b ONTRA-300
```

####Finishing work on a branch
`gitwork --finish`
Does the following:
```sh
git push origin [whatever_current_branch_is]
git checkout dev
git branch -D [whatever_current_branch_was]
```
To avoid deleting the branch:
`gitwork --finish n`


####Extras
`gitwork --show`
Will open your browser and take you to the jira ticket the current branch is named after.

###git config settings
settings configurable using git config command

```
gitwork.branch -- The priamray branch to update and create new branches from
gitwork.remote -- The name of the remote to update to/from
gitwork.delete -- Delete / don't delete a branch after it's been pushed to the remote, "1" will cause a delete, anything else will skip the delete.
gitwork.jiraurl -- Set the base level domain for jira e.g. 'https://jira.ontraport.com'
```

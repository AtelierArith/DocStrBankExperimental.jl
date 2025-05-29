```
CodeOwners <: Plugin
CodeOwners(; owners)
```

A plugin which created GitLab/GitHub compatible CODEOWNERS files. owners should be a vector of patterns mapped to a vector of owner names. For example: `owners=["*"=>["@invenia"], "README.md"=>["@documentation","@oxinabox]]` assigns general ownership over all files to the invenia group, but assigns ownership of the readme to the documentation group and to the user oxinabox.

By default, it creates an empty CODEOWNERS file.

```
struct GitHubProject
    owner::String
    package::String
    branch::String
    basedir::String
end
```

This structure holds details about a GitHub project we will be downloading information from.

**Values:**

| Name    | Description                                            |
|:------- |:------------------------------------------------------ |
| owner   | The owner of the project.                              |
| package | The package to look in.                                |
| branch  | The branch to use.                                     |
| basedir | The directory in the package to look for the files in. |

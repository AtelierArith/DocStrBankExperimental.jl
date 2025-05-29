```julia
struct Repo
```

Data structure representing a git repository.  This is associated with a particular path on the local file system, so it becomes invalid if the path is deleted.

## Examples

```julia
r = Repo("/path/to/repo")  # an existing repo
r = clone("https://path/to/repo.git", "newrepo")  # clone from remote and return repo

r = Repo("/phat/to/NOT/repo")  # will error on non-repo unless validate=false

mkdir("newnewrepo")
r = init("newnewrepo")  # create a new git repo
```

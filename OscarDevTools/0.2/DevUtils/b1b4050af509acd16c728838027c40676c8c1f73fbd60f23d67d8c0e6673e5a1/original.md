```
oscar_develop(pkgs::Array{String}; <keyword arguments>)
oscar_develop(pkgs::Dict{String,Any}; <keyword arguments>)
```

For each of the Oscar packages given in `pkgs`, create a new checkout in `dir`, and try to create new tracking branches for *existing* upstream branches `branch` (or fall back to `master`).

*Note:* To create new branches for a new feature please use [`oscar_branch`](@ref).

If `fork` is given the branch will be looked up in `https://github.com/fork/pkg.jl` and a second remote is created automatically; in addition to `origin` which will always point to the main repository.

The push-urls are set to `git@github.com:org-name/PackageName.jl` to facilitate pushing via ssh (both for `origin` and the optional `fork`).

These package checkouts are then added (dev'd) to a new julia project in `dir/project` which you can then use by running julia with:

```
julia --project=dir/project
```

# Arguments

  * `pkgs`: list of packages to operate on, please omit the `.jl`.
  * `branch::String="master"`: branch for checkout.
  * `dir="oscar-dev"`: development subdirectory.
  * `fork=nothing`: github organisation/user for branch lookup for all packages.
  * `active_repo=nothing`: used in CI to reuse the existing checkout of that package, corresponding to the github variable `$GITHUB_REPOSITORY`.
  * `merge=false`: used for CI: if `true` try to merge the latest `origin/master` into each checked out project; or any other branch if given a String specifying a `LibGit2.GitAnnotated`. Please note that this will not create the merge-commit (similar to `--no-commit`).

Each package name can optionally contain a branchname and a fork url:

  * `PackageName#somebranch` will checkout `somebranch` from the default upstream.
  * `PackageName#https://github.com/myfork/PackageName.jl#otherbranch` will use the `myfork` user for this package.

The package name and branch can also be given as dictionary mapping `PackageName.jl` to `[forkurl#]branchname`.

# Examples

```julia-repl
julia> oscar_develop(["Oscar","Polymake"]; branch="some_feature")
```

```julia-repl
julia> oscar_develop(["Oscar","Singular#more_rings"]; dir="dev_more_rings")
```

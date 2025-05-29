```
analyze(name_or_dir_or_url::AbstractString; registry=general_registry(), auth::GitHub.Authorization=github_auth(), version=nothing)
```

Analyze the package pointed to by the mandatory argument and return a summary of its properties.

  * If `name_or_dir_or_url` is a valid Julia identifier, it is assumed to be the name of a

package available in `registry`.  The function then uses [`find_package`](@ref) to find its entry in the registry and analyze the content of its latest registered version (or a different version, if the keyword argument `version` is supplied).

  * If `name_or_dir_or_url` is a filesystem path, analyze the package whose source code is

located at `name_or_dir_or_url`.

  * Otherwise, `name_or_dir_or_url` is assumed to be a URL. The repository is cloned to a temporary directory and analyzed.

If the GitHub authentication is non-anonymous and the repository is on GitHub, the list of contributors to the repository is also collected.  Only the number of contributors will be shown in the summary.  See [`PackageAnalyzer.github_auth`](@ref) to obtain a GitHub authentication.

!!! warning
    For packages in subdirectories, top-level information (like CI scripts) is only available when `name_or_dir_or_url` is a URL, or `name_or_dir_or_url` is a name and `version = :dev`. In other cases, the top-level code is not accessible.


## Example

You can analyze a package just by its name, whether you have it installed locally or not:

```julia
julia> analyze("Pluto"; version=v"0.18.0")
PackageV1 Pluto:
  * repo: https://github.com/fonsp/Pluto.jl.git
  * uuid: c3e4b0f8-55cb-11ea-2926-15256bba5781
  * version: 0.18.0
  * is reachable: true
  * tree hash: db1306745717d127037c5697436b04cfb9d7b3dd
  * Julia code in `src`: 8337 lines
  * Julia code in `test`: 5448 lines (39.5% of `test` + `src`)
  * documention in `docs`: 0 lines (0.0% of `docs` + `src`)
  * documention in README: 118 lines
  * has license(s) in file: MIT
    * filename: LICENSE
    * OSI approved: true
  * has license(s) in Project.toml: MIT
    * OSI approved: true
  * has `docs/make.jl`: false
  * has `test/runtests.jl`: true
  * has continuous integration: true
    * GitHub Actions

```

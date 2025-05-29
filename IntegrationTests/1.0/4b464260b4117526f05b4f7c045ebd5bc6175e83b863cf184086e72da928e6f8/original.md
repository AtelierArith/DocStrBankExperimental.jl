```
build_dependency_graph(
    info::Union{Pkg.API.ProjectInfo,Pkg.API.PackageInfo}=Pkg.project(),
    visited_packages::AbstractVector{String}=Vector{String}(),
)::Dict{String,Union{Dict,Nothing}}
```

Construct the dependency graph of the currently active project.

# Arguments

  * `project_info::Union{Pkg.API.ProjectInfo,Pkg.API.PackageInfo}`: properties about the current        project and Julia packages, such as name and version
  * `visited_packages::AbstractVector{String}`: list of packages that have already been processed

# Returns

Dependency diagram of the active project, stored in a `Dict`. The key is always the package name.  The value is either a `Dict` if the package has dependencies or `nothing` if there are no dependencies. If a package is a dependency more than once, only the first appearance has dependencies.  All other appearances have no dependencies. Standard library packages are ignored.

```
depending_projects(
    package_name::AbstractString, 
    package_filter::Union{<:AbstractString,Regex}
    project_tree::AbstractDict=build_dependency_graph()
)::Vector{String}
```

Returns a list of packages that have the package `package_name` as a dependency. 

# Arguments

  * `package_name`: Name of the dependency
  * `package_filter`: Ignore all packages that do not match `package_filter`. This includes the        top node package of the graph. Child nodes are always checked for `package_name`, but        they are not traversed if they do not match `package_filter`.
  * `project_tree`: Project tree in which to search for dependent packages. Each (sub-)package        needs to be `AbstractDict{String, AbstractDict}`

# Returns

A `Vector{String}` containing the names of all packages that have the given dependency.

```
depending_projects(
    package_name::AbstractString, 
    package_filter::AbstractVector{<:AbstractString}, 
    project_tree::AbstractDict=build_dependency_graph()
)::Vector{String}
```

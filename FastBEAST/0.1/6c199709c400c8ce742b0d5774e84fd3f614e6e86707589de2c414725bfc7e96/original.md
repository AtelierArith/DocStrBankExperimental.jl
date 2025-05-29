```
create_tree(points::Array{SVector{D, T}, 1}; treeoptions)
```

Creates an algebraic tree for an givn set of datapoints. The returned  datastructure is the foundation for the algorithms in this package. 

# Arguments

  * `points::Array{SVector{D, T}, 1}`: is an array of    [SVector](https://juliaarrays.github.io/StaticArrays.jl/stable/pages/api/#SVector-1).    Each    [SVector](https://juliaarrays.github.io/StaticArrays.jl/stable/pages/api/#SVector-1)   contains in general two or three float values, which discribe the position    in the space.

# Keywords

  * `treeoptions::TreeOptions`: this keyword defines by which tree is build.    `TreeOptions` is an abstract type which either can be `BoxTreeOptions` or   [`KMeansTreeOptions`](@ref). Default type is `BoxTreeOptions`.

# Returns

  * `AbstractNode`: the root of the created tree. AbstractNode is an abstract type    which either can be `BoxTreeNode` or [`KMeansTreeNode`](@ref), depending on the keyword.

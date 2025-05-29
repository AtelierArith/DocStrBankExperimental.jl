```
targets([f], data, [obsdim])
```

Extract the concrete targets from `data` and return them.

This function is eager in the sense that it will always call [`getobs`](@ref) unless a custom method for [`gettargets`](@ref) is implemented for the type of `data`. This will make sure that actual values are returned (in contrast to placeholders such as `DataSubset` or `SubArray`).

```julia
julia> targets(DataSubset([1,2,3]))
3-element Array{Int64,1}:
 1
 2
 3
```

If `data` is a tuple, then the convention is that the last element of the tuple contains the targets and the function is recursed once (and only once).

```julia
julia> targets(([1,2], [3,4]))
2-element Array{Int64,1}:
 3
 4

julia> targets(([1,2], ([3,4], [5,6])))
([3,4],[5,6])
```

If `f` is provided, then [`gettarget`](@ref) will be applied to each observation in `data` and the results will be returned as a vector.

```julia
julia> targets(argmax, [1 0 1; 0 1 0])
3-element Array{Int64,1}:
 1
 2
 1
```

The optional parameter `obsdim` can be used to specify which dimension denotes the observations, if that concept makes sense for the type of `data`. See `?ObsDim` for more information.

```julia
julia> targets(argmax, [1 0; 0 1; 1 0], obsdim=1)
3-element Array{Int64,1}:
 1
 2
 1
```

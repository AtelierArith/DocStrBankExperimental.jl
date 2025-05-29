```
load(filename::AbstractString)
```

Read a BVH file with name `filename` and return a `BVHGraph`.

# Examples

```julia
julia> g = load("Test.bvh")
BVHGraph
Name: Test.bvh
[...]
```

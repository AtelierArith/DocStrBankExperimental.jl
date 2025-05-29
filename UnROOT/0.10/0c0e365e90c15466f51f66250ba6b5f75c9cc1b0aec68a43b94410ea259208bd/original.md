```
LazyBranch(f::ROOTFile, branch)
```

Construct an accessor for a given branch such that `BA[idx]` and or `BA[1:20]` is type-stable. And memory footprint is a single basket (<1MB usually). You can also iterate or map over it. If you want a concrete `Vector`, simply `collect()` the LazyBranch.

# Example

```julia
julia> rf = ROOTFile("./test/samples/tree_with_large_array.root");

julia> b = rf["t1/int32_array"];

julia> ab = UnROOT.LazyBranch(rf, b);

julia> for entry in ab
           @show entry
           break
       end
entry = 0

julia> ab[begin:end]
0
1
...
```

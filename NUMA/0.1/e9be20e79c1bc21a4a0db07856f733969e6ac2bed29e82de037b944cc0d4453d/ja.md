ビットマスクを表します。ノードマスクやCPUマスクを示すために使用されます。

**例:**

```julia
julia> bm = Bitmask()
Bitmask (trunc): 00000000

julia> fill!(bm, 1); bm
Bitmask (trunc): 11111111

julia> bm[2] = 0; bm
Bitmask (trunc): 11111101

julia> numa_set_membind(bm)

julia> numa_get_membind()
Bitmask (trunc): 11111101
```

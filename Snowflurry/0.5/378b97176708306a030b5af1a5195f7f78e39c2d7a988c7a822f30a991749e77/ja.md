```
print_connectivity(
    connectivity::LatticeConnectivity,
    path::Vector{Int} = Vector{Int}(),
    io::IO = stdout,
)
```

`connectivity`を`io`に出力します。

`path`内のインデックスを持つ量子ビットが強調表示されます。

# 例

```jldoctest
julia> connectivity=LatticeConnectivity(3,3);

julia> path = path_search(1, 3, connectivity);

julia> print_connectivity(connectivity, path)
     (1)
      | 
 7 ──(4)── 2 
      |    | 
     (8)──(5)──(3)
           |    | 
           9 ── 6 

```

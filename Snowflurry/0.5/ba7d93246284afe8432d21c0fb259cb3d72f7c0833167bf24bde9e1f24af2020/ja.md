```
print_connectivity(
    connectivity::LineConnectivity,
    ::Vector{Int} = Int[],
    io::IO = stdout
)
```

`connectivity`を`io`に出力します。

`path`内のインデックスを持つキュービットが強調表示されます。

# 例

```jldoctest
julia> print_connectivity(LineConnectivity(3))
1──2──3

```

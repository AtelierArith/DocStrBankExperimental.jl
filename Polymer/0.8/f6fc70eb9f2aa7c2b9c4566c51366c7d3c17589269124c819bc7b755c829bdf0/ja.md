```
χNMatrix(m)
```

相互作用ペアの辞書を相互作用行列に変換します。入力引数 `m` は `Dict{Tuple{Symobl}, <:Real}`、`Dict{Tuple{String}, <:Real}`、`Dict{<:AbstractArray{Symbol}, <:Real}`、`Dict{<:AbstractArray{String}, <:Real}` のいずれかの辞書であることができます。

例:

```julia
map = Dict((:A, :B)=>10.0, (:A, :C)=>20.0, (:B, :C)=>30.0)
map = Dict(("A", "B")=>10.0, ("A", "C")=>20.0, ("B", "C")=>30.0)
map = Dict([:A, :B]=>10, [:A, :C]=>10.0, [:B, :C]=>20.0)
map = Dict(["A", "B"]=>10.0, ["A", "C"]=>20.0, ["B", "C"]=>30.0)
```

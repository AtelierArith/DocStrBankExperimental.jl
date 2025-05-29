```
tensor(v::Array{T,2}; dtype=Float64, sparse=false) where T
```

汎用配列 `v` をテンソルに変換します。例えば、

```julia
v = [0.0 constant(1.0) 2.0
    constant(2.0) 0.0 1.0]
u = tensor(v)
```

`u` は $2\times 3$ テンソルになります。

!!! note
    この関数は高コストです。使用には注意してください。


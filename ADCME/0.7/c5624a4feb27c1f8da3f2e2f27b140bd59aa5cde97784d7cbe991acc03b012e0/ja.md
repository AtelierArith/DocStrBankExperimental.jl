```
ae(x::PyObject, output_dims::Array{Int64}, scope::String = "default";
    activation::Union{Function,String} = "tanh")
```

エイリアス: `fc`, `ae`

中間のニューロン数 `output_dims` を持つニューラルネットワークを作成します。

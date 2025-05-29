```
MultiModel(models)
MultiModel(models, :SomeLabel)
```

多くの名前付きサブモデルから構成されるモデルのバリアントであり、それぞれが完全に実現された [`SimulationModel`](@ref) です。

`models` は `NamedTuple` または `Dict{Symbol, JutulModel}` である必要があります。

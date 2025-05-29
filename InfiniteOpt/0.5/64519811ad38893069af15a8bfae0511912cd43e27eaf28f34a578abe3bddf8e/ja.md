```
JuMP.mode(model::InfiniteModel)
```

`mode`を拡張して、最適化モデルがある`MathOptInterface`モードを返すようにします。

**例**

```julia-repl
julia> mode(model)
AUTOMATIC::ModelMode = 0
```

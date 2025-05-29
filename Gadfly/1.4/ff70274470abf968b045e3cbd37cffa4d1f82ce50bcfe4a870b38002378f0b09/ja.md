```
layer(f::Function, lower::Number, upper::Number,
      elements::ElementOrFunction...) -> [Layers]
```

関数または式 `f` からレイヤーを作成します。これは、`lower` と `upper` の境界の間で単一の引数を取るか、単一の変数で操作します。 [`Stat.func`](@ref) および [`Geom.line`](@ref) を参照してください。

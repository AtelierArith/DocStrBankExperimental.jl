```
plot(f::Function, lower::Number, upper::Number, elements::ElementOrFunction...;
     mapping...)
```

関数または式 `f` をプロットします。これは、単一の引数を取るか、単一の変数で操作します。範囲は `lower` と `upper` の境界の間です。 [`Stat.func`](@ref) および [`Geom.line`](@ref) を参照してください。

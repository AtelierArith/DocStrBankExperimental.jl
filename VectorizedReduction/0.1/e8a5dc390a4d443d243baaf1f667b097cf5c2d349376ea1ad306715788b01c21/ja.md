```
vvreduce(op, init, A::AbstractArray, dims=:)
```

バイナリ関数 `op` を使用して、次元 `dims` にわたって `A` を縮小します。 `op`、`init`、`dims` の説明については `vvmapreduce` を参照してください。

関連項目: [`vvsum`](@ref), [`vvprod`](@ref), [`vvminimum`](@ref), [`vvmaximum`](@ref)

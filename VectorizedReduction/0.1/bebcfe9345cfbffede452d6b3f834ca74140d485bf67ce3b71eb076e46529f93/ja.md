```
vtreduce(op, init, A::AbstractArray, dims=:)
```

バイナリ関数 `op` を使用して、次元 `dims` に沿って `A` を縮小します。 `op`、`init`、`dims` の説明については `vtmapreduce` を参照してください。

関連項目: [`vtsum`](@ref), [`vtprod`](@ref), [`vtminimum`](@ref), [`vtmaximum`](@ref)

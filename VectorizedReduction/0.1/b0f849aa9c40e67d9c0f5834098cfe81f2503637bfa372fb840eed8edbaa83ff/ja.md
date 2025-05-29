```
vtmapreduce(f, op, init, A::AbstractArray, dims=:)
```

関数 `f` を配列 `A` の各要素に適用し、次に二項関数 `op` を使用して次元 `dims` にわたって結果を縮約します。スレッド対応です。`dims` の説明については `vvmapreduce` を参照してください。`op` が `+`、`*`、`min`、`max` のいずれかである場合、`init` を提供する必要はありません。

参照: [`vtsum`](@ref), [`vtprod`](@ref), [`vtminimum`](@ref), [`vtmaximum`](@ref)

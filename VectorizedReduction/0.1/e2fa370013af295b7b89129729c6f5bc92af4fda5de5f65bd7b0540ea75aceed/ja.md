```
vtfindmax(f, A::AbstractArray, dims=:) -> (f(x), index)
```

引数の値とインデックスを返します。これは、次元 `dims` にわたって `f` を最大化します。`dims` は `::Int`、`::NTuple{M, Int} where {M}` または `::Colon` である可能性があります。スレッド対応です。

関連情報: [`vfindmax`](@ref)

# 警告

`NaN` 値は処理されません！

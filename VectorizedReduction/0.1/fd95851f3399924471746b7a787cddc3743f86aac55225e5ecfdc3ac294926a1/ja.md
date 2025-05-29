```
vtargmin(f, A::AbstractArray, dims=:)
```

引数のインデックスを返します。これは、次元 `dims` にわたって `f` を最小化します。`dims` は `::Int`、`::NTuple{M, Int} where {M}` または `::Colon` である可能性があります。スレッド対応です。

関連情報: [`vargmin`](@ref)

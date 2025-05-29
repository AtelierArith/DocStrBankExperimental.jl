```
範囲

範囲(; kw...)
範囲(bounds::NamedTuple)
```

オブジェクトの各次元の下限と上限を保持するタプルの `NamedTuple` のラッパーです。

`keys(extent)` は、オブジェクトで使用される次元の順序で次元名のシンボルを返します。

`values(extent)` は、各次元のタプル `(lowerbound, upperbound)` を返します。

# 例

```julia-repl
julia> ext = 範囲(X = (1.0, 2.0), Y = (3.0, 4.0))
範囲(X = (1.0, 2.0), Y = (3.0, 4.0))

julia> keys(ext)
(:X, :Y)

julia> values(ext)
((1.0, 2.0), (3.0, 4.0))
```

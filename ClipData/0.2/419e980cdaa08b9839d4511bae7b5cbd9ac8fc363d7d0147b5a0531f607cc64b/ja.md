```
cliparray(t::AbstractVecOrMat; kwargs...)
```

`Vector` または `Matrix` をクリップボードに送ります。デフォルトの区切り文字はタブで、ヘッダーはありません。`CSV.write` に渡すことができるすべてのキーワード引数を受け付けます。

# 例

```julia-repl
julia> """
       1 2
       3 4
       """ |> clipboard

julia> cliparray()
2×2 Matrix{Int64}:
 1  2
 3  4
```

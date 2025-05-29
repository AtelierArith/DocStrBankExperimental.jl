```
cliparray(; kwargs...)
```

クリップボードから `Vector` または `Matrix` を作成します。区切り文字を自動検出し、すべてのキーワード引数は `CSV.File` コンストラクタに直接渡されます。返された `CSV.File` に1列しかない場合、`cliparray` は `Vector` を返します。それ以外の場合は `Matrix` を返します。

# 例

```julia-repl
julia> # 文字列をクリップボードに送信
       """
       1 2
       3 4
       """ |> clipboard

julia> cliparray()
2×2 Matrix{Int64}:
 1  2
 3  4

julia> """
       1
       2
       3
       4
       """ |> clipboard

julia> cliparray()
4-element Vector{Int64}:
 1
 2
 3
 4
```

```
@passmissing(args...)
```

DataFramesMeta.jl マクロ内で欠損値を伝播させます。

`@passmissing` は「本物の」Juliaマクロではなく、DataFramesMeta.jl によって作成された操作を表す無名関数が Missings.jl の `passmissing` でラップされるべきであることを示す「フラグ」として機能します。

`@passmissing` は `@byrow` または `@rtransform` や `@rselect` などの行単位のマクロのバージョンとのみ組み合わせることができます。DataFramesMeta.jl によって `@byrow` で作成された行単位の無名関数に渡される引数のいずれかが欠損している場合、結果は自動的に `missing` になります。

以下の例では、`@transform` は `@passmissing` フラグなしではエラーを投げます。

`@passmissing` は、`parse` のように文字列に対して操作を行う関数に特に便利です。

### 例

```
julia> no_missing(x::Int, y::Int) = x + y;

julia> df = DataFrame(a = [1, 2, missing], b = [4, 5, 6])
3×2 DataFrame
 Row │ a        b
     │ Int64?   Int64
─────┼────────────────
   1 │       1      4
   2 │       2      5
   3 │ missing      6

julia> @transform df @passmissing @byrow c = no_missing(:a, :b)
3×3 DataFrame
 Row │ a        b      c
     │ Int64?   Int64  Int64?
─────┼─────────────────────────
   1 │       1      4        5
   2 │       2      5        7
   3 │ missing      6  missing

julia> df = DataFrame(x_str = ["1", "2", missing])
3×1 DataFrame
 Row │ x_str
     │ String?
─────┼─────────
   1 │ 1
   2 │ 2
   3 │ missing

julia> @rtransform df @passmissing x = parse(Int, :x_str)
3×2 DataFrame
 Row │ x_str    x
     │ String?  Int64?
─────┼──────────────────
   1 │ 1              1
   2 │ 2              2
   3 │ missing  missing
```

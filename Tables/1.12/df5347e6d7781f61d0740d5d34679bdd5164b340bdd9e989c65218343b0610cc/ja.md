```
Tables.rows(x) => 行イテレータ
```

入力テーブルソース `x` のデータに行ごとにアクセスし、[`AbstractRow`](@ref) 互換のイテレータを返します。入力テーブルソースが本質的に列指向であっても、`Tables.rows` の効率的な一般定義が Tables.jl に定義されており、入力の列への行ビューのイテレータを返します。

`AbstractRow` イテレータの [`Tables.Schema`](@ref) は `Tables.schema(rows)` を介して照会でき、スキーマが不明な場合は `nothing` を返すことがあります。列名は、個々の行に対して `Tables.columnnames(row)` を呼び出すことで常に照会でき、行の値には `Tables.getcolumn(row, i::Int )` または `Tables.getcolumn(row, nm::Symbol)` を呼び出すことで、列インデックスまたは名前を使ってアクセスできます。

[`rowtable`](@ref) および [`namedtupleiterator`](@ref) も参照してください。

```
Tables.columns(x) => AbstractColumns互換オブジェクト
```

入力テーブルソース `x` のデータにアクセスするために、[`AbstractColumns`](@ref) 互換オブジェクトを返します。これにより、名前またはインデックスで全列を取得できます。取得された列は1ベースのインデックス可能なオブジェクトで、既知の長さを持ち、すなわち `length(col)` および `col[i]` を任意の `i = 1:length(col)` に対してサポートします。入力テーブルソースが本質的に行指向であっても、入力行から `AbstractColumns` 互換オブジェクトを構築するために、Tables.jl で効率的な一般的定義の `Tables.columns` が定義されています。

`AbstractColumns` オブジェクトの [`Tables.Schema`](@ref) は `Tables.schema(columns)` を介して照会でき、スキーマが不明な場合は `nothing` を返すことがあります。列名は常に `Tables.columnnames(columns)` を呼び出すことで照会でき、個々の列には `Tables.getcolumn(columns, i::Int )` または `Tables.getcolumn(columns, nm::Symbol)` を呼び出すことで、列インデックスまたは名前を使ってアクセスできます。

`x` が列がベクトルとして格納されているオブジェクトである場合、これらのベクトルが1ベースのインデックスを使用しているかどうかのチェックは行われません（`x` が構築される際に確認する必要があります）。

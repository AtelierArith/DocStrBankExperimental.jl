```
subset(df::AbstractDataFrame, args...;
       skipmissing::Bool=false, view::Bool=false, threads::Bool=true)
subset(gdf::GroupedDataFrame, args...;
       skipmissing::Bool=false, view::Bool=false,
       ungroup::Bool=true, threads::Bool=true)
```

データフレーム `df` または `gdf` の親のコピーを返し、与えられた行に対して変換 `args` によって生成されたすべての値が `true` である行のみを含みます。すべての変換は `true` または `false` を含むベクトルを生成する必要があります。最初の引数が `GroupedDataFrame` の場合、変換は単一の `true` または `false` 値を返すことも許可されており、これによりグループ全体を含めるか除外することができます。

`skipmissing=false`（デフォルト）の場合、`args` は `Bool` 値のみを含む結果を生成する必要があります。`skipmissing=true` の場合、さらに `missing` が許可され、これは `false` として扱われます（つまり、条件のいずれかが `missing` を返す行はスキップされます）。

`args` に渡される各引数は、[`select`](@ref) に記載されたルールに従う任意の指定子であることができますが、次の制限があります：

  * 対象の列名を指定することはできません。`subset` は新しい列を作成しないためです。
  * 渡されたすべての変換はスカラーまたはベクトルを返す必要があります（`AbstractDataFrame`、`NamedTuple`、`DataFrameRow` または `AbstractMatrix` を返すことはサポートされていません）。

`view=true` の場合、`DataFrame` の代わりに `SubDataFrame` ビューが返されます。

`ungroup=false` の場合、結果のデータフレームは `gdf` と同じグループ化列に基づいて再グループ化され、`GroupedDataFrame` が返されます（`gdf` からのグループの順序を保持します）。

`threads=true`（デフォルト）の場合、変換は並行して実行できる別のタスクで実行される可能性があります（同時に複数の行またはグループに適用される可能性があります）。タスクが実際に生成されるかどうか、およびその数は自動的に決定されます。いくつかの変換が直列実行を必要とする場合やスレッドセーフでない場合は、`false` に設定してください。

`GroupedDataFrame` が渡された場合、それは `parent` データフレームに存在するすべてのグループを含む必要があります。これは [`select!`](@ref) と同様です。

!!! note
    `subset` 関数は DataFrames.jl で定義された他の変換関数とまったく同じように動作するため、データフレームまたはグループ化データフレームの行をサブセット化するための推奨される方法です。特に、これは [`filter`](@ref) とは異なる変換の指定ルールを使用しており、これはコレクションの標準 Julia API のサポートを確保するために DataFrames.jl で実装されています。


メタデータ：この関数はテーブルレベルおよび列レベルの `:note` スタイルのメタデータを保持します。

参照： [`subset!`](@ref), [`filter`](@ref), [`select`](@ref)

# 例

```jldoctest
julia> df = DataFrame(id=1:4, x=[true, false, true, false],
                      y=[true, true, false, false],
                      z=[true, true, missing, missing], v=[1, 2, 11, 12])
4×5 DataFrame
 Row │ id     x      y      z        v
     │ Int64  Bool   Bool   Bool?    Int64
─────┼─────────────────────────────────────
   1 │     1   true   true     true      1
   2 │     2  false   true     true      2
   3 │     3   true  false  missing     11
   4 │     4  false  false  missing     12

julia> subset(df, :x)
2×5 DataFrame
 Row │ id     x     y      z        v
     │ Int64  Bool  Bool   Bool?    Int64
─────┼────────────────────────────────────
   1 │     1  true   true     true      1
   2 │     3  true  false  missing     11

julia> subset(df, :v => x -> x .> 3)
2×5 DataFrame
 Row │ id     x      y      z        v
     │ Int64  Bool   Bool   Bool?    Int64
─────┼─────────────────────────────────────
   1 │     3   true  false  missing     11
   2 │     4  false  false  missing     12

julia> subset(df, :x, :y => ByRow(!))
1×5 DataFrame
 Row │ id     x     y      z        v
     │ Int64  Bool  Bool   Bool?    Int64
─────┼────────────────────────────────────
   1 │     3  true  false  missing     11

julia> subset(df, :x, :z, skipmissing=true)
1×5 DataFrame
 Row │ id     x     y     z      v
     │ Int64  Bool  Bool  Bool?  Int64
─────┼─────────────────────────────────
   1 │     1  true  true   true      1

julia> subset(df, :x, :z)
ERROR: ArgumentError: missing was returned in condition number 2 but only true or false are allowed; pass skipmissing=true to skip missing values

julia> subset(groupby(df, :y), :v => x -> x .> minimum(x))
2×5 DataFrame
 Row │ id     x      y      z        v
     │ Int64  Bool   Bool   Bool?    Int64
─────┼─────────────────────────────────────
   1 │     2  false   true     true      2
   2 │     4  false  false  missing     12

julia> subset(groupby(df, :y), :v => x -> minimum(x) > 5)
2×5 DataFrame
 Row │ id     x      y      z        v
     │ Int64  Bool   Bool   Bool?    Int64
─────┼─────────────────────────────────────
   1 │     3   true  false  missing     11
   2 │     4  false  false  missing     12
```

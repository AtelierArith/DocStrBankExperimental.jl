```
subset!(df::AbstractDataFrame, args...;
        skipmissing::Bool=false, threads::Bool=true)
subset!(gdf::GroupedDataFrame{DataFrame}, args...;
        skipmissing::Bool=false, ungroup::Bool=true, threads::Bool=true)
```

データフレーム `df` または `gdf` の親をインプレースで更新し、与えられた行に対して変換 `args` によって生成されるすべての値が `true` である行のみを含むようにします。すべての変換は `true` または `false` を含むベクトルを生成する必要があります。最初の引数が `GroupedDataFrame` の場合、変換は単一の `true` または `false` 値を返すことも許可されており、これにより全体のグループを含めるか除外することができます。

`skipmissing=false`（デフォルト）の場合、`args` は `Bool` 値のみを含む結果を生成する必要があります。`skipmissing=true` の場合、追加で `missing` が許可され、これは `false` として扱われます（つまり、条件のいずれかが `missing` を返す行はスキップされます）。

`args` に渡される各引数は、[`select`](@ref) に記載されたルールに従う任意の指定子であることができますが、次の制限があります：

  * 対象の列名を指定することはできません。`subset!` は新しい列を作成しないためです。
  * 渡されたすべての変換はスカラーまたはベクトルを返す必要があります（`AbstractDataFrame`、`NamedTuple`、`DataFrameRow` または `AbstractMatrix` を返すことはサポートされていません）。

`ungroup=false` の場合、渡された `GroupedDataFrame` `gdf` は更新され（そのグループの順序を保持）、返されます。

`threads=true`（デフォルト）の場合、変換は別のタスクで実行され、並行して実行される可能性があります（同時に複数の行またはグループに適用される可能性があります）。タスクが実際に生成されるかどうか、およびその数は自動的に決定されます。いくつかの変換が直列実行を必要とする場合やスレッドセーフでない場合は、`false` に設定してください。

`GroupedDataFrame` がサブセット化される場合、`parent` データフレームに存在するすべてのグループを含む必要があります。これは [`select!`](@ref) と同様です。この場合、親が更新された後に渡された `GroupedDataFrame` は正しいグループを持つように更新されます。

!!! note
    `subset!` 関数は DataFrames.jl で定義された他の変換関数とまったく同じように動作するため、データフレームまたはグループ化されたデータフレームの行をサブセット化するための推奨される方法です。特に、これは [`filter!`](@ref) とは異なる変換の指定ルールを使用しており、これは Julia のコレクションの標準 API をサポートするために DataFrames.jl で実装されています。


メタデータ：この関数はテーブルレベルおよび列レベルの `:note` スタイルのメタデータを保持します。

参照： [`subset`](@ref)、[`filter!`](@ref)、[`select!`](@ref)

# 例

```jldoctest
julia> df = DataFrame(id=1:4, x=[true, false, true, false], y=[true, true, false, false])
4×3 DataFrame
 Row │ id     x      y
     │ Int64  Bool   Bool
─────┼─────────────────────
   1 │     1   true   true
   2 │     2  false   true
   3 │     3   true  false
   4 │     4  false  false

julia> subset!(df, :x, :y => ByRow(!));

julia> df
1×3 DataFrame
 Row │ id     x     y
     │ Int64  Bool  Bool
─────┼────────────────────
   1 │     3  true  false

julia> df = DataFrame(id=1:4, y=[true, true, false, false], v=[1, 2, 11, 12]);

julia> subset!(groupby(df, :y), :v => x -> x .> minimum(x));

julia> df
2×3 DataFrame
 Row │ id     y      v
     │ Int64  Bool   Int64
─────┼─────────────────────
   1 │     2   true      2
   2 │     4  false     12

julia> df = DataFrame(id=1:4, x=[true, false, true, false],
                      z=[true, true, missing, missing], v=1:4)
4×4 DataFrame
 Row │ id     x      z        v
     │ Int64  Bool   Bool?    Int64
─────┼──────────────────────────────
   1 │     1   true     true      1
   2 │     2  false     true      2
   3 │     3   true  missing      3
   4 │     4  false  missing      4

julia> subset!(df, :x, :z)
ERROR: ArgumentError: missing was returned in condition number 2 but only true or false are allowed; pass skipmissing=true to skip missing values

julia> subset!(df, :x, :z, skipmissing=true);

julia> df
1×4 DataFrame
 Row │ id     x     z      v
     │ Int64  Bool  Bool?  Int64
─────┼───────────────────────────
   1 │     1  true   true      1

julia> df = DataFrame(id=1:4, x=[true, false, true, false], y=[true, true, false, false],
                      z=[true, true, missing, missing], v=[1, 2, 11, 12]);

julia> subset!(groupby(df, :y), :v => x -> x .> minimum(x));

julia> df
2×5 DataFrame
 Row │ id     x      y      z        v
     │ Int64  Bool   Bool   Bool?    Int64
─────┼─────────────────────────────────────
   1 │     2  false   true     true      2
   2 │     4  false  false  missing     12

julia> df = DataFrame(id=1:4, x=[true, false, true, false], y=[true, true, false, false],
                      z=[true, true, missing, missing], v=[1, 2, 11, 12]);

julia> subset!(groupby(df, :y), :v => x -> minimum(x) > 5);

julia> df
2×5 DataFrame
 Row │ id     x      y      z        v
     │ Int64  Bool   Bool   Bool?    Int64
─────┼─────────────────────────────────────
   1 │     3   true  false  missing     11
   2 │     4  false  false  missing     12
```

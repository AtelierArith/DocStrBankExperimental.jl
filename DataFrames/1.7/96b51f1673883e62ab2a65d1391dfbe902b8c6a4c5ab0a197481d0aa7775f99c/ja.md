```
describe(df::AbstractDataFrame; cols=:)
describe(df::AbstractDataFrame, stats::Union{Symbol, Pair}...; cols=:)
```

データフレームの記述統計を新しい `DataFrame` として返します。各行は変数を表し、各列は要約統計を表します。

# 引数

  * `df` : `AbstractDataFrame`
  * `stats::Union{Symbol, Pair}...` : 報告する要約統計。引数は次のようになります：

      * `:mean`, `:std`, `:min`, `:q25`, `:median`, `:q75`, `:max`, `:sum`, `:eltype`, `:nunique`, `:nuniqueall`, `:first`, `:last`, `:nnonmissing`, `:nmissing` のリストからのシンボル。デフォルトの統計は `:mean`, `:min`, `:median`, `:max`, `:nmissing`, `:eltype` です。
      * `:detailed` を唯一の `Symbol` 引数として指定すると、`:first`, `:last`, `:sum`, `:nuniqueall`, `:nnonmissing` を除くすべての統計が返されます。
      * `:all` を唯一の `Symbol` 引数として指定すると、すべての統計が返されます。
      * `function => name` のペアで、`name` は `Symbol` または文字列です。これにより、提供された名前の要約統計の列が作成されます。
  * `cols` : `df` から記述する列のサブセットまたは変換を選択するためのキーワード引数。[`select`](@ref) によって受け入れられる任意の列セレクタまたは変換が可能です。

# 詳細

`Real` 列の場合、平均、標準偏差、最小値、第一四分位数、中央値、第三四分位数、最大値を計算します。列が `Real` から派生していない場合、`describe` はすべての統計を計算しようとし、エラーが発生した場合は `nothing` をフォールバックとして使用します。

`stats` に `:nunique` が含まれている場合、`describe` は列内のユニークな値の数を報告します。列の基本型が `Real` から派生している場合、`:nunique` は `nothing` を返します。すべての列のユニークな値の数を報告するには `:nuniqueall` を使用します。

欠損値はすべての統計の計算でフィルタリングされますが、列 `:nmissing` はその変数の欠損値の数を報告し、`:nnonmissing` は非欠損値の数を報告します。

カスタム関数が提供されると、それらは各列に対応するベクトルを唯一の引数として繰り返し呼び出されます。欠損値を許可する列の場合、ベクトルは `skipmissing` の呼び出しでラップされます。したがって、カスタム関数はそのようなオブジェクト（ベクトルだけでなく）をサポートし、欠損値にアクセスすることはできません。

メタデータ：この関数はすべてのメタデータを削除します。

# 例

```jldoctest
julia> df = DataFrame(i=1:10, x=0.1:0.1:1.0, y='a':'j');

julia> describe(df)
3×7 DataFrame
 Row │ variable  mean    min  median  max  nmissing  eltype
     │ Symbol    Union…  Any  Union…  Any  Int64     DataType
─────┼────────────────────────────────────────────────────────
   1 │ i         5.5     1    5.5     10          0  Int64
   2 │ x         0.55    0.1  0.55    1.0         0  Float64
   3 │ y                 a            j           0  Char

julia> describe(df, :min, :max)
3×3 DataFrame
 Row │ variable  min  max
     │ Symbol    Any  Any
─────┼────────────────────
   1 │ i         1    10
   2 │ x         0.1  1.0
   3 │ y         a    j

julia> describe(df, :min, sum => :sum)
3×3 DataFrame
 Row │ variable  min  sum
     │ Symbol    Any  Union…
─────┼───────────────────────
   1 │ i         1    55
   2 │ x         0.1  5.5
   3 │ y         a

julia> describe(df, :min, sum => :sum, cols=:x)
1×3 DataFrame
 Row │ variable  min      sum
     │ Symbol    Float64  Float64
─────┼────────────────────────────
   1 │ x             0.1      5.5
```

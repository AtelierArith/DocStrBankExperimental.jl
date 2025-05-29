# 要約統計量

```julia
describe(ts::TSFrame; cols=:)
describe(ts::TSFrame, stats::Union{Symbol, Pair}...; cols=:)
```

`ts`の要約統計量を計算します。出力は、欠損値の数と列のデータ型を含む標準統計量を含む`DataFrame`です。`cols`キーワードは、`ts`から選択する列のサブセットを制御します。`stats`キーワードは、印刷する要約統計量を制御するために使用されます。これらのキーワードに関する詳細は、対応する[DataFrames.jlのドキュメント](https://dataframes.juliadata.org/stable/lib/functions/#DataAPI.describe)を参照してください。

# 例

```jldoctest; setup = :(using TSFrames, DataFrames, Dates, Random, Statistics)
julia> using Random;
julia> random(x) = rand(MersenneTwister(123), x...);
julia> ts = TSFrame(random(([1, 2, 3, 4, missing], 10)))
julia> describe(ts)
2×7 DataFrame
 Row │ variable  mean     min    median   max    nmissing  eltype
     │ Symbol    Float64  Int64  Float64  Int64  Int64     Type
─────┼───────────────────────────────────────────────────────────────────────────
   1 │ Index        5.5       1      5.5     10         0  Int64
   2 │ x1           2.75      2      3.0      4         2  Union{Missing, Int64}
julia> describe(ts, cols=:Index)
1×7 DataFrame
 Row │ variable  mean     min    median   max    nmissing  eltype
     │ Symbol    Float64  Int64  Float64  Int64  Int64     DataType
─────┼──────────────────────────────────────────────────────────────
   1 │ Index         5.5      1      5.5     10         0  Int64
julia> describe(ts, :min, :max, cols=:x1)
1×3 DataFrame
 Row │ variable  min    max
     │ Symbol    Int64  Int64
─────┼────────────────────────
   1 │ x1            2      4
julia> describe(ts, :min, sum => :sum)
2×3 DataFrame
 Row │ variable  min    sum
     │ Symbol    Int64  Int64
─────┼────────────────────────
   1 │ Index         1     55
   2 │ x1            2     22
julia> describe(ts, :min, sum => :sum, cols=:x1)
1×3 DataFrame
 Row │ variable  min    sum
     │ Symbol    Int64  Int64
─────┼────────────────────────
   1 │ x1            2     22

```

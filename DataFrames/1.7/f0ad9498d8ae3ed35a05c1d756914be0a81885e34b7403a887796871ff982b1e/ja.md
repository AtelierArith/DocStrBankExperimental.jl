```
unique!(df::AbstractDataFrame; keep::Symbol=:first)
unique!(df::AbstractDataFrame, cols; keep::Symbol=:first)
```

`df` をインプレースで更新して、ユニークな行のみを含むようにします。

非ユニーク（重複）行とは、少なくとも別の行が `cols` のすべての列に対して等しい値を持つ（`isequal` に従って）行のことです（デフォルトでは、すべての列）。`keep=:first`（デフォルト）であれば、重複行のセットの最初の出現のみが保持されます。`keep=:last` であれば、重複行のセットの最後の出現のみが保持されます。`keep=:noduplicates` であれば、重複のない行のみが保持されます。

# 引数

  * `df` : AbstractDataFrame
  * `cols` : 比較する列を指定する列インジケーター（`Symbol`、`Int`、`Vector{Symbol}`、`Regex` など）。`df` に少なくとも1つの列がある場合、少なくとも1つの列を返す [`select`](@ref) によって受け入れられる任意の列セレクターまたは変換を使用できます。

メタデータ: この関数は、テーブルレベルおよび列レベルの `:note` スタイルのメタデータを保持します。

関連情報: [`unique!`](@ref)、[`nonunique`](@ref)。

# 例

```jldoctest
julia> df = DataFrame(i=1:4, x=[1, 2, 1, 2])
4×2 DataFrame
 Row │ i      x
     │ Int64  Int64
─────┼──────────────
   1 │     1      1
   2 │     2      2
   3 │     3      1
   4 │     4      2

julia> df = vcat(df, df)
8×2 DataFrame
 Row │ i      x
     │ Int64  Int64
─────┼──────────────
   1 │     1      1
   2 │     2      2
   3 │     3      1
   4 │     4      2
   5 │     1      1
   6 │     2      2
   7 │     3      1
   8 │     4      2

julia> unique!(copy(df))  # df を修正
4×2 DataFrame
 Row │ i      x
     │ Int64  Int64
─────┼──────────────
   1 │     1      1
   2 │     2      2
   3 │     3      1
   4 │     4      2

julia> unique(df, keep=:noduplicates)
0×2 DataFrame
 Row │ i      x
     │ Int64  Int64
─────┴──────────────
```

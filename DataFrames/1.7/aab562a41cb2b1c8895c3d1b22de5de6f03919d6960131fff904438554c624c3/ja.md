```
nonunique(df::AbstractDataFrame; keep::Symbol=:first)
nonunique(df::AbstractDataFrame, cols; keep::Symbol=:first)
```

`true` エントリが重複行を示す `Vector{Bool}` を返します。

重複行とは、少なくとも別の行が `cols` のすべての列に対して等しい値を持つ行のことです（デフォルトではすべての列）。`keep=:first`（デフォルト）の場合、重複行のセットの最初の出現のみが `false` エントリで示されます。`keep=:last` の場合、重複行のセットの最後の出現のみが `false` エントリで示されます。`keep=:noduplicates` の場合、重複のない行のみが `false` エントリで示されます。

# 引数

  * `df` : `AbstractDataFrame`
  * `cols` : 比較する列またはその変換を指定するセレクタ。`df` に少なくとも1つの列がある場合、少なくとも1つの列を返す [`select`](@ref) によって受け入れられる任意の列セレクタまたは変換である必要があります。

他に [`unique`](@ref) および [`unique!`](@ref) も参照してください。

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

julia> nonunique(df)
8-element Vector{Bool}:
 0
 0
 0
 0
 1
 1
 1
 1

julia> nonunique(df, keep=:last)
8-element Vector{Bool}:
 1
 1
 1
 1
 0
 0
 0
 0

julia> nonunique(df, 2)
8-element Vector{Bool}:
 0
 0
 1
 1
 1
 1
 1
 1
```

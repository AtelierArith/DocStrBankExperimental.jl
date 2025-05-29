```
crossjoin(df1::AbstractDataFrame, df2::AbstractDataFrame;
          makeunique::Bool=false, renamecols=identity => identity)
crossjoin(df1, df2, dfs...; makeunique = false)
```

2つ以上のデータフレームオブジェクトのクロスジョインを実行し、結果を含む`DataFrame`を返します。クロスジョインは、すべての渡されたデータフレームの行のデカルト積を返し、最初に渡されたデータフレームが最も遅く変化する次元に割り当てられ、最後のデータフレームが最も速く変化する次元に割り当てられます。

# 引数

  * `df1`, `df2`, `dfs...` : 結合される`AbstractDataFrames`

# キーワード引数

  * `makeunique` : `false`（デフォルト）の場合、結合されていない列に重複名が見つかった場合にエラーが発生します。`true`の場合、重複名には`_i`が接尾辞として付加されます（`i`は最初の重複のために1から始まります）。
  * `renamecols` : 左側と右側のデータフレームの列が結果のデータフレームでどのように名前を変更されるべきかを指定する`Pair`。ペアの各要素は文字列または`Symbol`であり、その場合は元の列名に追加されます。あるいは、関数を渡すこともでき、その場合は各列名に適用され、`String`として渡されます。

2つ以上のデータフレームが渡された場合、結合は左結合的に再帰的に行われます。

メタデータ: テーブルレベルの`:note`スタイルのメタデータは、すべての渡されたテーブルで定義され、同じ値を持つキーに対してのみ保持されます。列レベルの`:note`スタイルのメタデータは、両方のテーブルから保持されます。

参照: [`innerjoin`](@ref), [`leftjoin`](@ref), [`rightjoin`](@ref),           [`outerjoin`](@ref), [`semijoin`](@ref), [`antijoin`](@ref).

# 例

```jldoctest
julia> df1 = DataFrame(X=1:3)
3×1 DataFrame
 Row │ X
     │ Int64
─────┼───────
   1 │     1
   2 │     2
   3 │     3

julia> df2 = DataFrame(Y=["a", "b"])
2×1 DataFrame
 Row │ Y
     │ String
─────┼────────
   1 │ a
   2 │ b

julia> crossjoin(df1, df2)
6×2 DataFrame
 Row │ X      Y
     │ Int64  String
─────┼───────────────
   1 │     1  a
   2 │     1  b
   3 │     2  a
   4 │     2  b
   5 │     3  a
   6 │     3  b
```

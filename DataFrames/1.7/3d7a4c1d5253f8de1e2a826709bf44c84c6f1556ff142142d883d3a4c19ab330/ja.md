```
append!(df::DataFrame, tables...; cols::Symbol=:setequal,
        promote::Bool=(cols in [:union, :subset]))
```

`tables`として渡された行を`df`の末尾に追加します。テーブルが`AbstractDataFrame`でない場合は、追加される前に`DataFrame(table, copycols=false)`を使用して変換されます。

`append!`の正確な動作は`cols`引数に依存します：

  * `cols == :setequal`（これがデフォルトです）の場合、`df2`は`df`とまったく同じ列を含む必要があります（ただし、順序は異なる可能性があります）。
  * `cols == :orderequal`の場合、`df2`は同じ順序で同じ列を含む必要があります（`AbstractDict`の場合、このオプションは`keys(row)`が`propertynames(df)`と一致する必要があり、順序付き辞書のサポートを可能にします。ただし、`df2`が`Dict`の場合、無秩序なコレクションであるためエラーが発生します）。
  * `cols == :intersect`の場合、`df2`は`df`よりも多くの列を含むことができますが、`df`に存在するすべての列名は`df2`にも存在しなければならず、これらのみが使用されます。
  * `cols == :subset`の場合、`append!`は`:intersect`のように動作しますが、`df2`にいくつかの列が欠けている場合、`df`に`missing`値が追加されます。
  * `cols == :union`の場合、`append!`は`df2`に存在するが`df`に欠けている列を追加し、`df`に存在するが`df2`に欠けている列には`missing`値が追加されます。

`promote=true`で、`df`に存在する列の要素型が追加される引数の型を許可しない場合、新しい列がプロモートされた要素型で新たに割り当てられ、`df`に保存されます。`promote=false`の場合、エラーが発生します。

上記のルールには以下の例外があります：

  * `df`に列がない場合、`df2`からの列のコピーが追加されます。
  * `df2`に列がない場合、`append!`を呼び出しても`df`は変更されません。

`append!`は、`===`で比較したときに等しい列がエイリアスである`DataFrame`に対して使用してはいけません。

メタデータ：テーブルレベルの`:note`スタイルのメタデータと、`df`に存在する列の列レベルの`:note`スタイルのメタデータは保持されます。新しい列が追加されると、その`:note`スタイルのメタデータは追加されたテーブルからコピーされます。他のメタデータは削除されます。

また、個々の行をデータフレームに追加するには[`push!`](@ref)を使用し、テーブルを先頭に追加するには[`prepend!`](@ref)を使用し、データフレームを垂直に連結するには[`vcat`](@ref)を使用してください。

# 例

```jldoctest
julia> df1 = DataFrame(A=1:3, B=1:3)
3×2 DataFrame
 Row │ A      B
     │ Int64  Int64
─────┼──────────────
   1 │     1      1
   2 │     2      2
   3 │     3      3

julia> df2 = DataFrame(A=4.0:6.0, B=4:6)
3×2 DataFrame
 Row │ A        B
     │ Float64  Int64
─────┼────────────────
   1 │     4.0      4
   2 │     5.0      5
   3 │     6.0      6

julia> append!(df1, df2);

julia> df1
6×2 DataFrame
 Row │ A      B
     │ Int64  Int64
─────┼──────────────
   1 │     1      1
   2 │     2      2
   3 │     3      3
   4 │     4      4
   5 │     5      5
   6 │     6      6

julia> append!(df2, DataFrame(A=1), (; C=1:2), cols=:union)
6×3 DataFrame
 Row │ A          B        C
     │ Float64?   Int64?   Int64?
─────┼─────────────────────────────
   1 │       4.0        4  missing
   2 │       5.0        5  missing
   3 │       6.0        6  missing
   4 │       1.0  missing  missing
   5 │ missing    missing        1
   6 │ missing    missing        2
```

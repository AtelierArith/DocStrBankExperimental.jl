```
insertcols!(df::AbstractDataFrame[, col], (name=>val)::Pair...;
            after::Bool=false, makeunique::Bool=false, copycols::Bool=true)
```

データフレームに列をインサートします。更新されたデータフレームを返します。

`col`が省略されると、`ncol(df)+1`に設定されます（列は最後の列として挿入されます）。

# 引数

  * `df` : 列を追加したいデータフレーム
  * `col` : 列を挿入したい位置。整数または列名（文字列または`Symbol`）として渡されます。`col`で選択された列とそれに続く列は、操作後に`df`内で右にシフトされます。
  * `name` : 新しい列の名前
  * `val` : 新しい列の内容を与える`AbstractVector`または、`AbstractArray`以外の任意の型の値で、新しいベクターを埋めるために繰り返されます。特に、`Ref`に格納された値や`0`次元の`AbstractArray`はアンラップされ、同じように扱われます。
  * `after` : `true`の場合、列は`col`の後に挿入されます。
  * `makeunique` : `name`がすでに`df`に存在する場合の処理を定義します。`false`の場合はエラーが発生します。`true`の場合は、サフィックスを追加して新しい一意の名前が生成されます。
  * `copycols` : 列として渡されたベクターをコピーするかどうか

`val`が`AbstractRange`の場合、`collect(val)`の結果が挿入されます。

`df`が`SubDataFrame`の場合、列セレクターとして`:`を使用して作成されている必要があります（そうでない場合はエラーが発生します）。この場合、`copycols`キーワード引数は無視され（つまり、追加された列は常にコピーされ）、親データフレームの列は`df`によってフィルタリングされた行に`missing`で埋められます。

`df`が列を持たない`DataFrame`で、`AbstractVector`以外の値が渡された場合、それは1要素の列を作成するために使用されます。`df`が列を持たない`DataFrame`で、少なくとも1つの`AbstractVector`が渡された場合、その長さが作成されるすべての列の要素数を決定するために使用されます。それ以外の場合、作成されるすべての列の行数は`nrow(df)`と一致する必要があります。

メタデータ：この関数は、テーブルレベルおよび列レベルの`:note`スタイルのメタデータを保持します。

他のスタイルのメタデータは削除されます（`df`が`SubDataFrame`の場合、親データフレームから）。

詳細は[`insertcols`](@ref)を参照してください。

# 例

```jldoctest
julia> df = DataFrame(a=1:3)
3×1 DataFrame
 Row │ a
     │ Int64
─────┼───────
   1 │     1
   2 │     2
   3 │     3

julia> insertcols!(df, 1, :b => 'a':'c')
3×2 DataFrame
 Row │ b     a
     │ Char  Int64
─────┼─────────────
   1 │ a         1
   2 │ b         2
   3 │ c         3

julia> insertcols!(df, 2, :c => 2:4, :c => 3:5, makeunique=true)
3×4 DataFrame
 Row │ b     c      c_1    a
     │ Char  Int64  Int64  Int64
─────┼───────────────────────────
   1 │ a         2      3      1
   2 │ b         3      4      2
   3 │ c         4      5      3

julia> insertcols!(df, :b, :d => 7:9, after=true)
3×5 DataFrame
 Row │ b     d      c      c_1    a
     │ Char  Int64  Int64  Int64  Int64
─────┼──────────────────────────────────
   1 │ a         7      2      3      1
   2 │ b         8      3      4      2
   3 │ c         9      4      5      3
```

```
sort(df::AbstractDataFrame, cols=All();
     alg::Union{Algorithm, Nothing}=nothing,
     lt::Union{Function, AbstractVector{<:Function}}=isless,
     by::Union{Function, AbstractVector{<:Function}}=identity,
     rev::Union{Bool, AbstractVector{Bool}}=false,
     order::Union{Ordering, AbstractVector{<:Ordering}}=Forward,
     view::Bool=false,
     checkunique::Bool=false)
```

`df`の行を`cols`列でソートしたデータフレームを返します。複数の列でのソートは辞書式に行われます。

`cols`は任意の列セレクタ（`Symbol`、文字列または整数；`:`, `Cols`, `All`, `Between`, `Not`、正規表現、または`Symbol`、文字列または整数のベクター）を指定できます。`cols`が列を選択しない場合、すべての列で`df`をソートします（この動作は非推奨であり、将来のバージョンで変更される予定です）。

`rev`が`true`の場合、逆順ソートが行われます。特定の列に対してのみ逆順ソートを有効にするには、`cols`に`order(c, rev=true)`を渡します。ここで`c`は対応する列のインデックスです（以下の例を参照）。

重複要素があると複数のソート順が有効になるため、`checkunique`キーワードを使用してその状況を検出できます。`checkunique`が`true`で重複要素が見つかった場合、エラーがスローされます。`by`または`lt`キーワードが使用されていない場合にのみ、`checkunique`キーワードの使用がサポートされます。同様に、`by`または`lt`を指定する`order(...)`句の使用はサポートされていませんが、`rev`を単独で指定することは許可されています。

`by`キーワードは、比較の前に各セルに適用される関数を提供することを可能にします；`lt`キーワードはカスタムの「小さい」関数を提供することを可能にします。`by`と`lt`の両方が指定された場合、`by`関数の結果に`lt`関数が適用されます。

ソート順を指定するキーワード引数（`rev`、`lt`または`by`）は、単一の値または操作が行われる列の数と同じ長さのベクターのいずれかであることができます。単一の値が渡されると、それはすべての列に適用されます。ベクターが渡されると、各エントリは`cols`の対応する位置の列に適用されます。

`alg`が`nothing`（デフォルト）である場合、ソート列のタイプと`df`の行数に応じて、最も適切なアルゴリズムが自動的に選択されます（`TimSort`、`MergeSort`、`RadixSort`の中から）。

`view=false`の場合、新しく割り当てられた`DataFrame`が返されます。`view=true`の場合、`df`への`SubDataFrame`ビューが返されます。

メタデータ：この関数は、テーブルレベルおよび列レベルの`:note`スタイルのメタデータを保持します。

# 例

```jldoctest
julia> df = DataFrame(x=[3, 1, 2, 1], y=["b", "c", "a", "b"])
4×2 DataFrame
 Row │ x      y
     │ Int64  String
─────┼───────────────
   1 │     3  b
   2 │     1  c
   3 │     2  a
   4 │     1  b

julia> sort(df, :x)
4×2 DataFrame
 Row │ x      y
     │ Int64  String
─────┼───────────────
   1 │     1  c
   2 │     1  b
   3 │     2  a
   4 │     3  b

julia> sort(df, [:x, :y])
4×2 DataFrame
 Row │ x      y
     │ Int64  String
─────┼───────────────
   1 │     1  b
   2 │     1  c
   3 │     2  a
   4 │     3  b

julia> sort(df, [:x, :y], rev=true)
4×2 DataFrame
 Row │ x      y
     │ Int64  String
─────┼───────────────
   1 │     3  b
   2 │     2  a
   3 │     1  c
   4 │     1  b

julia> sort(df, [:x, order(:y, rev=true)])
4×2 DataFrame
 Row │ x      y
     │ Int64  String
─────┼───────────────
   1 │     1  c
   2 │     1  b
   3 │     2  a
   4 │     3  b
```

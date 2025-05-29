```
mapcols(f::Union{Function, Type}, df::AbstractDataFrame; cols=All())
```

`df`の各列を`cols`（デフォルトではすべての列）で選択し、関数`f`を使用して変換した`DataFrame`を返します。`cols`で選択されていない列はコピーされます。

`f`はすべて同じ長さの`AbstractVector`オブジェクトまたはスカラーを返さなければなりません（`AbstractVector`以外のすべての値はスカラーと見なされます）。

`cols`の列セレクタは、`names`関数によって受け入れられる任意の値を指定できます。

`mapcols`は、返される`DataFrame`内で`df`の列を再利用しないことを保証します。`f`が引数を返す場合、それは保存される前にコピーされます。

メタデータ：この関数は、テーブルレベルおよび列レベルの`:note`スタイルのメタデータを保持します。

# 例

```jldoctest
julia> df = DataFrame(x=1:4, y=11:14)
4×2 DataFrame
 Row │ x      y
     │ Int64  Int64
─────┼──────────────
   1 │     1     11
   2 │     2     12
   3 │     3     13
   4 │     4     14

julia> mapcols(x -> x.^2, df)
4×2 DataFrame
 Row │ x      y
     │ Int64  Int64
─────┼──────────────
   1 │     1    121
   2 │     4    144
   3 │     9    169
   4 │    16    196

julia> mapcols(x -> x.^2, df, cols=r"y")
4×2 DataFrame
 Row │ x      y
     │ Int64  Int64
─────┼──────────────
   1 │     1    121
   2 │     2    144
   3 │     3    169
   4 │     4    196
```

```
mapcols!(f::Union{Function, Type}, df::DataFrame; cols=All())
```

`cols` で選択された `df` の各列が関数 `f` を使用して変換されるように、`DataFrame` をインプレースで更新します（デフォルトではすべての列）。`cols` で選択されていない列は変更されません。

`f` はすべて同じ長さの `AbstractVector` オブジェクトを返すか、スカラー（`AbstractVector` 以外のすべての値はスカラーと見なされます）でなければなりません。

`mapcols!` は、`f` によって返された場合、`df` から列を再利用します。

メタデータ: この関数は、テーブルレベルおよび列レベルの `:note` スタイルのメタデータを保持します。

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

julia> mapcols!(x -> x.^2, df);

julia> df
4×2 DataFrame
 Row │ x      y
     │ Int64  Int64
─────┼──────────────
   1 │     1    121
   2 │     4    144
   3 │     9    169
   4 │    16    196

julia> mapcols!(x -> 2 * x, df, cols=r"x");

julia> df
4×2 DataFrame
 Row │ x      y
     │ Int64  Int64
─────┼──────────────
   1 │     2    121
   2 │     8    144
   3 │    18    169
   4 │    32    196
```

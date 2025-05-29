```
reverse(df::AbstractDataFrame, start=1, stop=nrow(df))
```

`df`の行を逆順に含むデータフレームを返します。`start`と`stop`が指定されている場合、`start:stop`の範囲内の行のみが影響を受けます。

メタデータ: この関数は、テーブルレベルおよびカラムレベルの`:note`スタイルのメタデータを保持します。

# 例

```jldoctest
julia> df = DataFrame(a=1:5, b=6:10, c=11:15)
5×3 DataFrame
 Row │ a      b      c
     │ Int64  Int64  Int64
─────┼─────────────────────
   1 │     1      6     11
   2 │     2      7     12
   3 │     3      8     13
   4 │     4      9     14
   5 │     5     10     15

julia> reverse(df)
5×3 DataFrame
 Row │ a      b      c
     │ Int64  Int64  Int64
─────┼─────────────────────
   1 │     5     10     15
   2 │     4      9     14
   3 │     3      8     13
   4 │     2      7     12
   5 │     1      6     11

julia> reverse(df, 2, 3)
5×3 DataFrame
 Row │ a      b      c
     │ Int64  Int64  Int64
─────┼─────────────────────
   1 │     1      6     11
   2 │     3      8     13
   3 │     2      7     12
   4 │     4      9     14
   5 │     5     10     15
```

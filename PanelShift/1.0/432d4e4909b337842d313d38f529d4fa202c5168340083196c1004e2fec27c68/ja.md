```
panellag!(df, id, t, x, newx, n=oneunit(df[1, t] - df[1, t]); checksorted=true)
```

データフレーム `df` 内で、`id` によってインデックス付けされた各グループについて、時間列 `t` に関して `x` 列を `n` 期間遅らせ、新しい列 `newx` に遅延列を格納します。引数 `id`、`t`、`x`、および `newx` はすべて `df` の列インデックスです。

# 例

```jldoctest
julia> using DataFrames;
julia> df = DataFrame(
    t = [1;2;3;4; 1;3;4; 1;4; 1], 
    id = [1;1;1;1; 2;2;2; 3;3; 4],
    x = [1;2;3;4; 5;6;7; 8;9; 10]
);
julia> panellag!(df, :id, :t, :x, :Lx)

10×4 DataFrame
 Row │ t      id     x      Lx      
     │ Int64  Int64  Int64  Int64?  
─────┼──────────────────────────────
   1 │     1      1      1  missing 
   2 │     2      1      2        1
   3 │     3      1      3        2
  ⋮  │   ⋮      ⋮      ⋮       ⋮
   8 │     1      3      8  missing 
   9 │     4      3      9  missing 
  10 │     1      4     10  missing 
                      4 rows omitted


```

`panellead!`、`panelshift!` も参照してください。

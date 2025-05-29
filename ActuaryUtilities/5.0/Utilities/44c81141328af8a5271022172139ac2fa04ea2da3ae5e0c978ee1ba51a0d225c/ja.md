```
Years_Between(d1::Date, d2::Date)
```

2つの日付の間の整数年数を計算します。最初の日付は通常、2番目の日付の前にあります。最初の日付が2番目の日付の後の場合は負の数を返します。カレンダーの記念日が1年としてカウントされるべきかどうかを示すために、3番目の引数を使用します。

# 例

```julia
julia> d1 = Date(2018,09,30);

julia> d2 = Date(2019,09,30);

julia> d3 = Date(2019,10,01);

julia> years_between(d1,d3) 
1
julia> years_between(d1,d2,false) # 同じ月/日ですが `false` の重複
0 
julia> years_between(d1,d2) # 同じ月/日ですが `true` の重複
1 
julia> years_between(d1,d2) # デフォルトの `true` の重複を使用
1 
```

```
duration(d1::Date, d2::Date)
```

2つの日付が与えられたときの期間を計算します。これは最初の日付からの年数です。区間 `[0,1)` は期間 `1` を持つと定義されています。2番目の引数が最初の引数より前の場合、負の期間を返すことがあります。

```julia
julia> issue_date  = Date(2018,9,30);

julia> duration(issue_date , Date(2019,9,30) ) 
2
julia> duration(issue_date , issue_date) 
1
julia> duration(issue_date , Date(2018,10,1) ) 
1
julia> duration(issue_date , Date(2019,10,1) ) 
2
julia> duration(issue_date , Date(2018,6,30) ) 
0
julia> duration(Date(2018,9,30),Date(2017,6,30)) 
-1
```

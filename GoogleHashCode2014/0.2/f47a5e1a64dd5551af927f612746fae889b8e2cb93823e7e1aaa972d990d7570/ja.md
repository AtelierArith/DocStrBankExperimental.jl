```
is_street_start(i::Integer, street::Street)
```

交差点インデックス `i` が `street` の有効な開始点であるかを確認します。

# 例

```jldoctest
julia> using GoogleHashCode2014

julia> city = read_city();

julia> street = city.streets[10]
交差点インデックス 6814 と 2728 の間の双方向の通り - 所要時間 13秒、距離 187メートル

julia> is_street_start(6814, street)
true

julia> is_street_start(2728, street)
true

julia> street = city.streets[11]
交差点インデックス 3779 からインデックス 7853 への単方向の通り - 所要時間 12秒、距離 88メートル

julia> is_street_start(3779, street)
true

julia> is_street_start(7853, street)
false
```

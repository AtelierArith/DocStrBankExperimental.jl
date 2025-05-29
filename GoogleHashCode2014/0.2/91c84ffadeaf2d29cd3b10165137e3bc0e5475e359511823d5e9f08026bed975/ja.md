```
is_street(i::Integer, j::Integer, street::Street)
```

交差点インデックス `i` から交差点インデックス `j` への移動が `street` の有効な方向に対応しているかを確認します。

[`Street`](@ref) の有効な方向は次のとおりです：

  * `street.endpointA` から `street.endpointB` へのすべてのケース
  * `street.endpointB` から `street.endpointA` への移動は、`street.bidirectional` が `true` の場合のみ

# 例

```jldoctest
julia> using GoogleHashCode2014

julia> city = read_city(); 

julia> street = city.streets[10]
交差点インデックス 6814 と 2728 の間の双方向の通り - 所要時間 13秒、距離 187m

julia> is_street(1, 2728, street)
false

julia> is_street(6814, 2728, street)
true

julia> is_street(2728, 6814, street)
true

julia> street = city.streets[11]
交差点インデックス 3779 からインデックス 7853 への単方向の通り - 所要時間 12秒、距離 88m

julia> is_street(3779, 7853, street)
true

julia> is_street(7853, 3779, street)  # 双方向ではないため
false
```

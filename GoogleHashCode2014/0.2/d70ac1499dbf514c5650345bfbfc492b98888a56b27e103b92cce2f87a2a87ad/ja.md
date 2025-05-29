```
get_street_end(i::Integer, street::Street)
```

交差点インデックス `i` から始めて `street` の反対側の交差点インデックスを取得します。

もし `i` が `street` の有効な出発点でない場合、エラーが発生します。

# 例

```jldoctest
julia> using GoogleHashCode2014

julia> city = read_city();

julia> street = city.streets[10]
双方向の通り、交差点インデックス 6814 と 2728 の間 - 所要時間 13秒、距離 187m

julia> get_street_end(6814, street)
2728

julia> get_street_end(2728, street)
6814

julia> street = city.streets[11]
一方向の通り、交差点インデックス 3779 からインデックス 7853 への - 所要時間 12秒、距離 88m

julia> get_street_end(3779, street)
7853
```

```
ストリート
```

2つの交差点の間にエッジを[`City`](@ref)に保存します。

!!! tip
    `Street`は、[`Junction`](@ref)オブジェクト自体ではなく、整数インデックスを持つ交差点を指します。


# フィールド

  * `endpointA::Int`: 最初の交差点のインデックス
  * `endpointB::Int`: 2番目の交差点のインデックス
  * `bidirectional::Bool`: `B -> A`が許可されているかどうか
  * `duration::Int`: ストリートを通過するのにかかる時間コスト（秒単位）
  * `distance::Int`: ストリートの長さ（メートル単位）

# 例

```jldoctest
julia> using GoogleHashCode2014

julia> city = read_city();

julia> street = city.streets[10]
Bidirectional street between junction indices 6814 and 2728 - duration 13s, distance 187m

julia> street.bidirectional
true

julia> (street.endpointA, street.endpointB)
(6814, 2728)

julia> (street.distance / street.duration) * 3.6  # speed on that street in km/h
51.784615384615385

julia> street = city.streets[11]
Monodirectional street from junction index 3779 to index 7853 - duration 12s, distance 88m

julia> street.bidirectional
false
```

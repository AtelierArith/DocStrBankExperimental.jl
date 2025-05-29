```
detect_events(lgl::AbstractVector{Bool}; len_min=1, index=nothing, only_max=false, ignored...)
detect_events(y::AbstractVector{<:Real}, lgl::BitVector;
    len_min=1,
    len2peak=0,
    goal=1,
    index=nothing,
    only_max=false,
    ignored...
)
```

信号内のイベントを論理ベクトルに基づいて検出します。

# 引数

  * `y::AbstractVector{<:Real}`: イベントを検出する信号。
  * `lgl::BitVector`: 信号内でイベントが発生する場所を示す論理ベクトル。
  * `len_min=1`: (オプション) イベントの最小長。
  * `len2peak=0`: (オプション) ピークからイベントの始まりまたは終わりまでの最小長。
  * `goal=1`: (オプション)、`-1` または `1`。`1` の場合、イベント内の最大値を見つけます; `-1` の場合、最小値が使用されます。
  * `index=nothing`: (オプション) 信号のインデックス。提供された場合、返されるインデックスはインデックス空間内になります。
  * `only_max=false`: (オプション) `true` の場合、最大の持続時間を持つイベントのみが返されます。
  * `ignored...`: (オプション) 無視される引数。

# 戻り値

各タプルがイベントを表し、以下のフィールドを持つ名前付きタプルの配列:

  * `i_beg::Integer`: イベントの始まりのインデックス。
  * `i_peak::Integer`: イベントのピークのインデックス。
  * `i_end::Integer`: イベントの終わりのインデックス。
  * `len::Integer`: イベントの長さ。
  * `len_left::Integer`: イベントの始まりからピークまでの長さ。
  * `len_right::Integer`: ピークからイベントの終わりまでの長さ。
  * `peak::Real`: イベントのピークの値。

`only_max` が `true` の場合、最大の持続時間を持つイベントのみが返されます。

# 例

```julia
julia> y = [0, 1, 2, 3, 0, 2, 1, 0];
julia> lgl = y .> 0;
julia> detect_events(lgl)
2-element Vector{NamedTuple{(:i_beg, :i_end, :len), Tuple{Int64, Int64, Int64}}}:
 (i_beg = 2, i_end = 4, len = 3)
 (i_beg = 6, i_end = 7, len = 2)
julia> detect_events(y, lgl)
2-element Vector{NamedTuple{(:i_beg, :i_peak, :i_end, :len, :len_left, :len_right, :peak), NTuple{7, Int64}}}:
 (i_beg = 2, i_peak = 4, i_end = 4, len = 3, len_left = 2, len_right = 0, peak = 3)
 (i_beg = 6, i_peak = 6, i_end = 7, len = 2, len_left = 0, len_right = 1, peak = 2)
```

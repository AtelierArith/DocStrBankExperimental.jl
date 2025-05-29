```
extract_eventInfo(y::AbstractVector{<:Real}, i_beg::Integer, i_end::Integer;
    index=nothing, goal=1, len_min=1, len2peak=0, ignored...)
```

信号内のイベントに関する情報を抽出します。

# 例

```julia
julia> y = [0, 1, 2, 3, 2, 1, 0];
julia> extract_eventInfo(y, 2, 6)
(i_beg = 2, i_peak = 4, i_end = 5, len = 4, len_left = 2, len_right = 1, peak = 3)
```

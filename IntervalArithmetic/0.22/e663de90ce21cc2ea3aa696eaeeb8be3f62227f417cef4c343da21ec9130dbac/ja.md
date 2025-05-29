```
文字列 `"str"` を解析して区間を作成します。これは `parse(Interval{[DEFAULT BOUND TYPE]}, "str")` と意味的に同等です。

# 例

```

jldoctest julia> setdisplay(:full);

julia> I"[3, 4]" Interval{Float64}(3.0, 4.0, com)

julia> I"0.1" Interval{Float64}(0.09999999999999999, 0.1, com)

julia> in_interval(1//10, I"0.1") true ```

```
peakwidths!(; [strict, relheight, min, max]) -> Function
```

関数 `f(pks::NamedTuple)` を作成し、与えられたキーワード引数を使用して、引数 `pks` のピーク幅やその他のフィールドを計算し、フィルタリング（変異）します。

# 例

```jldoctest
julia> findmaxima([0,5,2,3,3,1,4,0]) |> peakproms!() |> peakwidths!(; min=1.5)
(indices = [4], heights = [3], data = [0, 5, 2, 3, 3, 1, 4, 0], proms = Union{Missing, Int64}[1], widths = Union{Missing, Float64}[1.75], edges = Tuple{Union{Missing, Float64}, Union{Missing, Float64}}[(3.5, 5.25)])
```

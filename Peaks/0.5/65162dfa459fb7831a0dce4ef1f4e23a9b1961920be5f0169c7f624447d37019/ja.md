```
peakproms(; [strict, min, max]) -> Function
```

引数 `pks` のコピーのピークのプロミネンスを計算し、与えられたキーワード引数を使用してフィルタリングする関数 `f(pks::NamedTuple)` を作成します。

# 例

```jldoctest
julia> findmaxima([0,5,2,3,3,1,4,0]) |> peakproms(; min=2)
(indices = [2, 7], heights = [5, 4], data = [0, 5, 2, 3, 3, 1, 4, 0], proms = Union{Missing, Int64}[5, 3])
```

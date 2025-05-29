```
peakheights!(; [min, max]) -> Function
```

関数 `f(pks::NamedTuple)` を作成し、ピークの高さを計算し、与えられたキーワード引数を使用して引数 `pks` のフィールドをフィルタリング（変異）します。

# 例

```jldoctest
julia> findmaxima([0, 5, 2, 3, 3, 1, 4, 0]) |> peakheights!(; max=4)
(indices = [4, 7], heights = [3, 4], data = [0, 5, 2, 3, 3, 1, 4, 0])
```

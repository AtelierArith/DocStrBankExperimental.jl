```
peakheights(; [min, max]) -> Function
```

引数 `pks` のピーク高さをコピーしてフィルタリングする関数 `f(pks::NamedTuple)` を作成します。任意のキーワード引数を使用します。

# 例

```jldoctest
julia> findmaxima([0, 5, 2, 3, 3, 1, 4, 0]) |> peakheights(; max=4)
(indices = [4, 7], heights = [3, 4], data = [0, 5, 2, 3, 3, 1, 4, 0])
```

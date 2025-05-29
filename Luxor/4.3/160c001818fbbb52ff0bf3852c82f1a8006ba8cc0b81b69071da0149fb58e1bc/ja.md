```
polysample(p::Vector{Point}, npoints::T where T <: Integer;
        closed=true)
```

ポリゴン `p` をサンプリングし、`npoints` を返してそれを表します。最初のサンプリングポイントは：

```1/`npoints` * `perimeter of p````

元の `p` の最初のポイントからの距離です。

`npoints` が `length(p)` と同じ場合、返されるポリゴンは元のものと同じですが、最初のポイントは最後に移動します（したがって `new=circshift(old, 1)`）。

`closed` が true の場合、ポリゴン全体（最後のポイントと最初のポイントを結ぶ辺を含む）がサンプリングされます。

`include_first` が true の場合、`plist` の最初のポイントが結果に含まれます。

結果のポリゴンの最初と最後のポイントが同じ場合、最後のポイントは破棄されます。

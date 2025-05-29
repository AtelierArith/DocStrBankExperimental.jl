```
molecule_centers(coords, boundary, topology)
```

システム内の各分子の中心の座標を計算します。

周期境界条件を考慮して円平均を使用します。`topology=nothing`の場合、座標が返されます。

トポロジーが設定されている場合、[`TriclinicBoundary`](@ref)とは現在互換性がありません。

```
pathtopolys(f::Paths.Segment{T}, s::Paths.Style; kwargs...)
```

セグメントとスタイルで表されたパスノードから、同等のポリゴンのセットを構築します。いくつかの線形セグメントとスタイルに対しては、`Polygon{T}`のセットで十分ですが、曲線のような他のものには`CurvilinearRegion{T}`が必要です。

これは、パスがスキマティックグラフの一部ではなく、コンポーネントの構築内で使用される場合に特に役立ちます。

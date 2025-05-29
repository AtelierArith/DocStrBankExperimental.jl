```
intersects(geometry₁, geometry₂)
```

`geometry₁` と `geometry₂` が交差するかどうかを示します。

## 参考文献

  * Gilbert, E., Johnson, D., Keerthi, S. 1988. [三次元空間における複雑なオブジェクト間の距離を計算するための高速手法](https://ieeexplore.ieee.org/document/2083)

### 注意事項

フォールバックアルゴリズムは、明確に定義された [`supportfun`](@ref) を持つ任意のジオメトリで機能します。

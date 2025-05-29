homography1d - 1D ホモグラフィを計算します

```
Usage:   H = homography1d(x1, x2)

Arguments:
         x1  - 2xN の同次点のセット
         x2  - x1<->x2 を満たす 2xN の同次点のセット
Returns:
          H - x2 = H*x1 を満たす 2x2 のホモグラフィ
```

このコードは、Hartley と Zisserman の p92 に記載されている 2D ホモグラフィの正規化直接線形変換アルゴリズムに基づいています。

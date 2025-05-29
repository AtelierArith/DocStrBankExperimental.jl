```
Fronts.DiffusionEquation(pm::UnsaturatedFlowModel)
Fronts.DiffusionEquation{m}(pm::UnsaturatedFlowModel)
```

与えられた不飽和流モデルで定義された水分拡散方程式（未知の `θ` を含む）。

# 引数

  * `pm`: 不飽和流モデル。

# 型パラメータ

  * `m=1`: 空間次元の数：

      * 非放射状の1次元拡散の場合は1（デフォルト）；
      * 極座標または円筒座標での放射状拡散の場合は2；
      * 球座標での放射状拡散の場合は3。

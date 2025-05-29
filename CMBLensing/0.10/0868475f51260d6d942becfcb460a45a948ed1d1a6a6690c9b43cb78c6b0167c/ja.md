```
kde(samples::AbstractVector; [boundary=(min,max), normalize="integral" or "max"])
kde(samples::AbstractMatrix; [boundary=[(min1,max1),(min2,max2)], normalize="integral" or "max", smooth_scale_2D])
```

1Dまたは2Dサンプルのセットに対するカーネル密度推定を返します。返されるオブジェクトは、PDFを計算するためにどこでも評価できる関数です。指定された場合、`boundary`は1または2のパラメータに対する厳密な上限/下限を指定し、`normalize`はPDFを単位積分または単位最大に正規化するかどうかを指定し、`smooth_scale_2D`は2Dの場合のスムージングの程度を指定します。

Pythonの[GetDist](https://getdist.readthedocs.io/en/latest/intro.html)に基づいており、インストールする必要があります。

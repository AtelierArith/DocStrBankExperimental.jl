```
canny_edges = canny(img, (upper, lower), sigma=1.4)
```

入力画像に対してCannyエッジ検出を実行します。

パラメータ :

(upper, lower) : ヒステリシスしきい値の境界   sigma :           ガウシアンフィルタの標準偏差を指定します

# 例

```julia
imgedg = canny(img, (Percentile(80), Percentile(20)))
```

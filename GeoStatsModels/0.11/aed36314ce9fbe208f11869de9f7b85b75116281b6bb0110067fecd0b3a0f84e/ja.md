```
IDW(exponent=1, distance=Euclidean())
```

シェパード1968によって地理統計学の初期に導入された逆距離加重モデル。

重みは、与えられた`distance`を`d`、`exponent`を`e`とした場合に、`λᵢ = 1 / d(x, xᵢ)ᵉ`として計算されます。

## 参考文献

  * シェパード1968. [不規則に配置されたデータのための二次元補間関数](https://dl.acm.org/doi/10.1145/800186.810616)

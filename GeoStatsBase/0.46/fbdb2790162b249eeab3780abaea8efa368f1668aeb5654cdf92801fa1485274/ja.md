```
hscatter(data, var₁, var₂; [options])
```

地理空間 `data` の変数 `var₁` と `var₂` のペアに対する H-散布図で、追加の `options` があります。

## アルゴリズムオプション:

  * `lag`      - 点間の遅延距離（長さ単位、デフォルトは `0.0u"m"`）
  * `tol`      - 遅延距離の許容誤差（長さ単位、デフォルトは `1e-1u"m"`）
  * `distance` - Distances.jl からの距離（デフォルトは `Euclidean()`）

## 美的オプション:

  * `size`   - 点セットの点のサイズ
  * `color`  - 幾何学または点の色
  * `alpha`  - [0,1] の透明度チャネル
  * `rcolor` - 回帰線の色
  * `icolor` - 同一線の色
  * `ccolor` - 中心線の色

## 例

```
# 遅延 1.0 の Z 対 Z の h-散布図
hscatter(data, :Z, :Z, lag=1.0)

# 遅延 2.0 の Z 対 W の h-散布図
hscatter(data, :Z, :W, lag=2.0)
```

```
ProjectedBasis(;L, N, base=2, alloc=1000, threaded=true)
```

固定粒子数（または総U(1)電荷）に対する`ProjectedBasis`の構築方法。

## 入力:

  * `dtype`   : インデックスのデータ型。
  * `L`       : 系の長さ。
  * `N`       : 上スピンの量子数 / 粒子数 / U(1)電荷。
  * `base`    : 基数、デフォルト = 2。
  * `alloc`   : 基底内容のための事前割り当てメモリのサイズ、マルチスレッドでのみ使用、デフォルト = 1000。
  * `threaded`: マルチスレッドを使用するかどうか、デフォルト = true。
  * `small_N` : small-Nアルゴリズムを使用するかどうか。

## 出力:

  * `b` : ProjectedBasis。

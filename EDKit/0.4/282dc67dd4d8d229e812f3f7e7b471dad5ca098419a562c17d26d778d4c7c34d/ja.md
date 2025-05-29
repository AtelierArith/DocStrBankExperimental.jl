```
TranslationalBasis(f, k, L; base=2, alloc=1000, threaded=true)
```

`TranslationalBasis`の構築。

## 入力:

  * `dtype`   : インデックスのデータ型。
  * `L`       : 系の長さ。
  * `f`       : 基底内容の選択関数。
  * `k`       : 0からL-1までの運動量番号。
  * `N`       : 粒子数。
  * `a`       : 単位セルの長さ。
  * `base`    : 基数、デフォルト = 2。
  * `alloc`   : 基底内容のための事前割り当てメモリのサイズ（マルチスレッド時のみ使用）、デフォルト = 1000。
  * `threaded`: マルチスレッドを使用するかどうか、デフォルト = true。

## 出力:

  * `b`: TranslationalBasis。

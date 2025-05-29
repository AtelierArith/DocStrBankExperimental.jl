TranslationFlipBasis(f, k, p, L; base=2, alloc=1000, threaded=true)

`TranslationFlipBasis`の構築。

## 入力:

  * `f`       : 基底内容の選択関数。
  * `k`       : 0からL-1までの運動量番号。
  * `p`       : パリティ番号（スピンフリップの下）±1。
  * `L`       : 系の長さ。
  * `base`    : 基数、デフォルト = 2。
  * `alloc`   : 基底内容のための事前割り当てメモリのサイズ、マルチスレッドでのみ使用、デフォルト = 1000。
  * `threaded`: マルチスレッドを使用するかどうか、デフォルト = true。

## 出力:

  * `b`: TranslationFlipBasis。

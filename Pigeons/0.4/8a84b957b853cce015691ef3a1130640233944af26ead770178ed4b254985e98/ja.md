スライスサンプラーは、[Neal, 2003](https://projecteuclid.org/journals/annals-of-statistics/volume-31/issue-3/Slice-sampling/10.1214/aos/1056562461.full)に基づいています。

フィールド:

  * `w`: 初期スライスサイズ。
  * `p`: スライスは2^p * wを超えない。
  * `n_passes`: 探索ステップごとにすべての変数を通過する回数。
  * `max_iter`: エラーが発生する前に`shrink_slice!`内での最大反復回数。

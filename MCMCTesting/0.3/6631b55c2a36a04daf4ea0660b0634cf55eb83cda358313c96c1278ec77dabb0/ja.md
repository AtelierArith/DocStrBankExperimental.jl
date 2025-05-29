```
seqmcmctest([rng,] test, subject, false_rejection_rate, samplesize; kwargs...)
```

連続的に複数の仮説検定を実行して `false_rejection_rate` を保証します。

# 引数

  * `rng::Random.AbstractRNG`: 擬似乱数生成器。
  * `test::AbstractMCMCTest`: テスト戦略。
  * `subject::TestSubject`: テスト対象のMCMCアルゴリズムとモデル。
  * `false_rejection_rate::Real`: 望ましい偽陽性率。
  * `samplesize::Int`: 各テスト反復で使用されるp値の数。

# キーワード引数

  * `samplesize_increase`: 最初のテスト反復が不確定な場合のサンプルサイズの増加係数。 (デフォルト: `2.0`)
  * `show_progress::Bool`: 進行状況を表示するかどうか。 (デフォルト: `true`)
  * `pvalue_adjustmeht::MultipleTesting.PValueAdjustment`: 統計量の要素に対する多重検定のためのp値調整。 (デフォルト: `MultipleTesting.Bonferroni()`)

追加のキーワード引数は、内部呼び出しの `mcmctest` に渡されます。

# 戻り値

  * `test_result::Bool`: 帰無仮説（MCMCアルゴリズムが正しい定常分布を持つ）が棄却されなかった場合は `true`、それ以外は `false`。

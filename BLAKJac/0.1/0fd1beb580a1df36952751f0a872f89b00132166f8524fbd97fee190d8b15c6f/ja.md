```
BLAKJac_optimize(trajectorySet, options::Dict, mersenneTwisterSeed=1)
```

BLAKJac による最適化手順

与えられた ky パターン（または (ky,kz)-パターン）といくつかのオプションに基づいて、最適化されたかのように見える RF パルスのシーケンスを生成します。シードパラメータは整数として提供でき、ランダム値の初期化の異なる実現を可能にします。（デフォルトでは、毎回同じシーケンスを再現可能に生成する必要があります）

意味のあるオプションのセットは、「options = Dict(); BLAKJac.BLAKJac_defaults!(trajectorySet, options)」によって事前に定義できます。

いくつかのオプションパラメータを理解するためには、最適化が二段階から成ることを知っておく必要があります（そのうちしばしば一段階のみが使用されます）。第一段階では、自由度の数が増加するにつれて、三次スプライン補間された滑らかな RF パターンを最適化します（「解像度の増加」）。第二段階では、最適化された「過去」を前提に、シーケンスの部分を部分ごとに最適化することによって、シーケンスの連続部分が「微調整」されます。

オプションパラメータは次のとおりです：

  * `nky`             ky の範囲
  * `sizeSteps`       整数の配列；第一段階での「解像度」を提供します
  * `portion_size`    最適化される部分のサイズ
  * `portion_step`    一つの部分が十分に最適化されたと見なされた後、「次の」部分が取り組まれます。これは `portion_step` だけ先に進みます。                   できれば、`portion_step` は `portion_size` より小さい方が望ましいです。
  * `opt_iterations_limit`  整数。第一段階と第二段階のステップの合計を制御します。第二段階をオフにするには、sizeSteps の長さにする必要があります。                     任意の高い値に設定すると「完全な処理」を意味します。
  * `opt_complex`     ブール。すべてのパルスに位相を持たせることを許可します。非推奨。
  * `opt_slow_phase`  ブール。位相を最適化する非常に制御された方法：最適化されるのは位相の二次導関数の低解像度です。
  * `opt_imposed_2nd_derivative_of_phase`        （nTR 要素のベクトル）位相の二次導関数を最適化しない場合に記入します -                                            すなわち、事前に定義されている場合。
  * `opt_initialize`  最適化に入る前に RF パターンがどのように最適化されるかを制御します。 `"ones"`（すべての角度が1度）、                      `"ernst"`（すべての角度が参照 T1 と TR に基づいて Ernst 角に設定される）、 `"init_angle"`（すべてが `opt_init_angle` に設定される）、                     `"cRandom30"`（30度の偏差を持つランダム値に設定される）または `"RF_shape"`（オプション                      `"rfFunction"` によって提供される初期形状）であることができます。
  * `rfFunction`      （上記参照）
  * `opt_init_angle`  （上記参照）
  * `opt_focus`       最適化者はどの特性に焦点を当てるべきですか？ `"rho"`、 `"T1"`、 `"T2"`、 `"mean"`、 `"max"` または `"weighted"` のいずれかであることができます；                      最後のものは T1ref および T2ref に対する T1 と T2 の *相対的* ノイズレベルを組み合わせます。
  * `opt_criterion`   `"noise_level"`、 `"low-flip corrected noise"`、 `"sar-limited noise"`、 `"information content"`、                  `"information content penalized"`、                    `"B1 sensitivity sar-limited"`、 `"B1 sensitivity/noise mix, sar-limited"` のいずれかであることができます。
  * `lambda_B1`       B1 感度の正則化パラメータ
  * `lambda_CSF`      CSF 感度の正則化パラメータ
  * `opt_keep_positive`   ブール。真の場合、負の角度は厳しく罰せられます。
  * `opt_emergeCriterion` 整数。opt_emergeCriterion 回の反復ごとに RF 形状の中間表示を呼び出します。
  * `opt_method`      最適化関数、例：NelderMead
  * `optpars`         最適化パラメータ - Optim パッケージを参照してください。

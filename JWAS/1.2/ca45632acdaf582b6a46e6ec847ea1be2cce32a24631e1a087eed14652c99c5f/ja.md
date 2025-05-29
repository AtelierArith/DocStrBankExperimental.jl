```
runMCMC(model::MME,df::DataFrame;
        #データ
        heterogeneous_residuals           = false,
        #MCMC
        chain_length::Integer             = 100,
        starting_value                    = false,
        burnin::Integer                   = 0,
        output_samples_frequency::Integer = chain_length>1000 ? div(chain_length,1000) : 1,
        update_priors_frequency::Integer  = 0,
        #メソッド
        estimate_variance               = true,
        single_step_analysis            = false, #単一ステップ分析のパラメータ
        pedigree                        = false, #単一ステップ分析のパラメータ
        fitting_J_vector                = true,  #単一ステップ分析のパラメータ
        categorical_trait               = false,
        censored_trait                  = false,
        causal_structure                = false,
        mega_trait                      = false,
        missing_phenotypes              = true,
        constraint                      = false,
        #ゲノム予測
        outputEBV                       = true,
        output_heritability             = true,
        prediction_equation             = false,
        #その他
        seed                            = false,
        printout_model_info             = true,
        printout_frequency              = chain_length+1,
        big_memory                      = false,
        double_precision                = false,
        ##MCMCサンプル（デフォルトはマーカー効果とハイパーパラメータ（分散成分））
        output_folder                     = "results",
        output_samples_for_all_parameters = false,
        ##非推奨のJWAS用
        methods                         = "conventional (no markers)",
        Pi                              = 0.0,
        estimatePi                      = false,
        estimateScale                   = false)
```

**分散成分の推定の有無にかかわらず、ベイジアン線形混合モデルのためのMCMCを実行します。**

  * マルコフ連鎖モンテカルロ

      * 最初の `burnin` イテレーションは、長さ `chain_length` のMCMCチェーンの開始時に破棄されます。
      * `output_samples_frequency` イテレーションごとにMCMCサンプルを保存し、デフォルトは `chain_length/1000` で、フォルダ `output_folder` に保存され、デフォルトは `results` です。ハイパーパラメータ（分散成分）とマーカー効果のMCMCサンプルはデフォルトで保存されます。位置パラメータのMCMCサンプルは、関数 `output_MCMC_samples()` を使用して保存できます。MCMCサンプルを頻繁に保存すると計算が遅くなることに注意してください。
      * `starting_value` は、すべての位置パラメータとマーカー効果のベクトルとして提供できます。デフォルトは `0.0` です。位置パラメータとマーカー効果の開始値の順序は、すべての特性の混合モデル方程式における位置パラメータの順序（これは getNames(model) で取得できます）に従い、その後すべての特性のマーカー（特性1のすべてのマーカー、その後特性2のすべてのマーカー...）の順序である必要があります。
      * その他のオプション

          * プライヤーは、デフォルトで `0` の `update_priors_frequency` イテレーションごとに更新されます。
  * メソッド

      * `single_step_analysis` = `true` で `pedigree` が提供されている場合、単一ステップ分析が許可されます。
      * `estimate_variance`=true の場合、分散成分が推定され、デフォルトは `true` です。
      * その他のオプション

          * `missing_phenotypes`=true の場合、マルチトレイト分析で欠損表現型が許可され、デフォルトは `true` です。
          * `categorical_trait`=true の場合、カテゴリカル特性が許可され、デフォルトは `false` です。表現型は 1,2,3... としてコーディングする必要があります。
          * 上限が `censored_trait` に配列として提供され、下限が表現型として提供される場合、検閲された特性が許可されます。
          * `constraint`=true の場合、デフォルトは `false` で、特性間の残差共分散をゼロに制約します。
          * `causal_structure` が提供されている場合、例えば、trait 1 -> trait 2 および trait 1 -> trait 3 のための causal_structure = [0.0 0.0 0.0;1.0 0.0 0.0;1.0 0.0 0.0]（列インデックスが行インデックスに影響し、下三角行列が必要です）、表現型因果ネットワークが構造方程式モデルを使用して組み込まれます。
  * ゲノム予測

      * ユーザー定義の予測方程式 `prediction_equation` に基づいて、関心のある個体の予測値を取得できます。例えば、"y1:animal + y1:age" です。

    現在、ゲノムデータは常に含まれています。遺伝子型と系譜情報で定義された効果を含む遺伝的値が返されます。`prediction_equation`= false の場合、デフォルトは `false` です。

      * `outputEBV`=true の場合、個々の推定遺伝的値と予測誤差分散（PEV）が返され、デフォルトは `true` です。遺伝率と遺伝的

    分散は `output_heritability`=`true` の場合に返され、デフォルトは `true` です。遺伝率の推定は計算集約的であることに注意してください。
  * その他のオプション

      * `printout_model_info`=true の場合、REPLにモデル情報を出力します。`printout_frequency` でモンテカルロ平均をREPLに出力し、デフォルトは `false` です。
      * `seed` が提供されている場合、デフォルトは `false` で、再現可能な数列が生成されます。
      * `big_memory`=true の場合、デフォルトは `false` で、大量のメモリを持つマシンが仮定され、分析が高速化される可能性があります。

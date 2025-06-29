```
PsisLoo <: AbstractCV
```

パレトスムーズ重要度サンプリングを用いて計算された、留一交差検証の結果を含む構造体です。

# フィールド

  * `estimates::KeyedArray`: 列 `:total, :se_total, :mean, :se_mean` と行 `:cv_elpd, :naive_lpd, :p_eff` を持つ KeyedArray。詳細は `# Extended help` を参照してください。

      * `:cv_elpd` には、留一交差検証を使用して推定された、サンプル外予測誤差の推定値が含まれています。
      * `:naive_lpd` には、サンプル内予測誤差の推定値が含まれています。
      * `:p_eff` は有効パラメータ数です。`p_eff` が 2 のモデルは、2つのパラメータを持ち正則化がないモデルと「ほぼ同じくらい過剰適合」しています。
  * `pointwise::KeyedArray`: 5列のポイントごとの推定値を持つ `KeyedArray` –

      * `:cv_elpd` には、このポイントの推定されたサンプル外誤差が含まれています。これは留一交差検証を使用して測定されます。
      * `:naive_lpd` には、このポイントのサンプル内誤差の推定値が含まれています。
      * `:p_eff` は前の2つの推定値の差です。
      * `:ess` はL2有効サンプルサイズで、モンテカルロ推定を使用することによって引き起こされるシミュレーション誤差を推定します。これはモデルのパフォーマンスを測定するものではありません。
      * `:inf_ess` は上限に基づく有効サンプルサイズで、モンテカルロ推定を使用することによって引き起こされるシミュレーション誤差を推定します。これは `:ess` よりも堅牢であるため、好まれるべきです。これもモデルのパフォーマンスを測定するものではありません。
      * `:pareto_k` は一般化パレート分布のパラメータ `ξ` の推定値です。0.7を超える値は、PSISが真の分布を近似することに失敗したことを示します。
  * `psis_object::Psis`: パレトスムーズ重要度サンプリングの結果を含む `Psis` オブジェクト。
  * `gmpd`: 予測密度の幾何平均です。これは、モデルによって各データポイントに割り当てられた確率の幾何平均として定義されます。すなわち、`exp(cv_avg)`。この指標は分類器（離散的な結果を持つ変数）に対してのみ解釈可能です。これは、モデルがどれだけ正確であったかを測定するものと考えることができます。常に誤って予測するモデルはGMPDが0になり、常に正しく予測するモデルはGMPDが1になります。ただし、GMPDは、モデルが実際に起こった結果に対して0または1以外の確率を割り当てるたびに、0と1の間の「部分点」をモデルに与えるため、モデルの質の完全なベイズ的指標となります。
  * `mcse`: 総交差検証推定のための推定モンテカルロ標準誤差を含む浮動小数点数。

# 拡張ヘルプ

総スコアはサンプルサイズに依存し、モデルに対する証拠の重みを要約します。総スコアは間隔尺度であり、スコアの差のみが意味を持ちます。*総スコアを見て解釈することはできません。* 総スコアは適合度統計ではありません（これについては平均スコアを参照してください）。

平均スコアは総スコアをサンプルサイズで割ったものです。これは、次のポイントを観測するための対数確率密度の期待値、すなわち期待対数スコアを推定します。平均スコアはサンプルサイズに依存しない相対的な適合度統計です。

カイ二乗適合度検定とは異なり、モデル比較のために交差検証手法を使用する場合、モデルはネストされている必要はありません。

参照: [`loo`]@ref, [`bayes_cv`]@ref, [`psis_loo`]@ref, [`Psis`]@ref

```
from_dict(posterior::AbstractDict; kwargs...) -> InferenceData
```

辞書を[`InferenceData`](@ref)に変換します。

# 引数

  * `posterior`: 変換されるデータ。文字列は`Symbol`または`AbstractString`でなければならず、その値は配列でなければなりません。

# キーワード

  * `posterior_predictive::Any=nothing`: 事後予測分布からのサンプリング
  * `sample_stats::Any=nothing`: 事後サンプリングプロセスの統計
  * `predictions::Any=nothing`: 事後の外部サンプル予測。
  * `prior::Dict=nothing`: 事前からのサンプリング
  * `prior_predictive::Any=nothing`: 事前予測分布からのサンプリング
  * `sample_stats_prior::Any=nothing`: 事前サンプリングプロセスの統計
  * `observed_data::NamedTuple`: `posterior`が条件となる観測データ。ランダム変数としてモデル化されるデータのみを含むべきです。キーはパラメータ名、値はデータです。
  * `constant_data::NamedTuple`: モデル定数、ランダム変数としてモデル化されないモデルに含まれるデータ。キーはパラメータ名、値はデータです。
  * `predictions_constant_data::NamedTuple`: モデル予測に関連する定数（すなわち、線形回帰における新しい`x`値）。
  * `log_likelihood`: データのポイントごとの対数尤度。この引数は、観測変数名をキーとし、対数尤度配列を値とする`NamedTuple`として使用することを推奨します。
  * `library`: サンプリングを生成したライブラリの名前
  * `coords`: 名前付き次元から名前付きインデックスへのマップ
  * `dims`: 変数名からその次元の名前へのマップ

# 戻り値

  * `InferenceData`: 提供されたデータに対応するグループを持つデータ

# 例

```@example
using InferenceObjects
nchains = 2
ndraws = 100

data = Dict(
    :x => rand(ndraws, nchains),
    :y => randn(2, ndraws, nchains),
    :z => randn(3, 2, ndraws, nchains),
)
idata = from_dict(data)
```

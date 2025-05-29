```
from_namedtuple(posterior::NamedTuple; kwargs...) -> InferenceData
from_namedtuple(posterior::Vector{Vector{<:NamedTuple}}; kwargs...) -> InferenceData
from_namedtuple(
    posterior::NamedTuple,
    sample_stats::Any,
    posterior_predictive::Any,
    predictions::Any,
    log_likelihood::Any;
    kwargs...
) -> InferenceData
```

`NamedTuple`または`NamedTuple`のコンテナを`InferenceData`に変換します。

コンテナが渡されると、それらは単一の`NamedTuple`にフラット化され、最初の次元がコンテナの次元に対応する配列要素を持ちます。

# 引数

  * `posterior`: 変換されるデータ。以下の型のいずれかである可能性があります：

      * `::NamedTuple`: キーは変数名で、値は次元が`(ndraws, nchains[, sizes...])`の配列です。
      * `::Vector{Vector{<:NamedTuple}}`: 長さ`nchains`のベクトルで、要素の長さは`ndraws`です。

# キーワード

  * `posterior_predictive::Any=nothing`: ポスターリオ予測分布からのサンプル
  * `sample_stats::Any=nothing`: ポスターリオサンプリングプロセスの統計
  * `predictions::Any=nothing`: ポスターリオの外挿予測。
  * `prior=nothing`: プライアからのサンプル。`posterior`と同じ型を受け入れます。
  * `prior_predictive::Any=nothing`: プライア予測分布からのサンプル
  * `sample_stats_prior::Any=nothing`: プライアサンプリングプロセスの統計
  * `observed_data::NamedTuple`: `posterior`が条件となる観測データ。ランダム変数としてモデル化されるデータのみを含むべきです。キーはパラメータ名、値はそれに対応します。
  * `constant_data::NamedTuple`: モデル定数、ランダム変数としてモデル化されないモデルに含まれるデータ。キーはパラメータ名、値はそれに対応します。
  * `predictions_constant_data::NamedTuple`: モデル予測に関連する定数（すなわち、線形回帰における新しい`x`値）。
  * `log_likelihood`: データのポイントごとの対数尤度。観測された変数名をキーとし、対数尤度配列を値とする`NamedTuple`としてこの引数を使用することを推奨します。
  * `library`: サンプルを生成したライブラリの名前
  * `coords`: 名前付き次元から名前付きインデックスへのマップ
  * `dims`: 変数名からその次元の名前へのマップ

# 戻り値

  * `InferenceData`: 提供されたデータに対応するグループを持つデータ

!!! 注     `observed_data`、`constant_data`、または`predictions_constant_data`に`NamedTuple`が提供される場合、非配列値（例：整数）は0次元配列に変換されます。

# 例

```@example
using InferenceObjects
nchains = 2
ndraws = 100

data1 = (
    x=rand(ndraws, nchains), y=randn(ndraws, nchains, 2), z=randn(ndraws, nchains, 3, 2)
)
idata1 = from_namedtuple(data1)

data2 = [[(x=rand(), y=randn(2), z=randn(3, 2)) for _ in 1:ndraws] for _ in 1:nchains];
idata2 = from_namedtuple(data2)
```

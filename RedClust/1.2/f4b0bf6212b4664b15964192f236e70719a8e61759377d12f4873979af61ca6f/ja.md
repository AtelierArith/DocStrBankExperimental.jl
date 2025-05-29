MCMCサンプルを含む構造体。

# フィールド

  * `options::MCMCOptionsList`: サンプラーに渡されるオプション。
  * `params::PriorHyperparamsList`: サンプラーによって使用される事前ハイパーパラメータ。
  * `clusts::Vector{ClustLabelVector}`: クラスタリングの割り当てを含む。`clusts[i]`は`i`番目のサンプルからのクラスタリング割り当てを含むベクトル。
  * `posterior_coclustering::Matrix{Float64}`: 事後コクラスタリング行列。
  * `K::Vector{Int}`: $K$の事後サンプル、すなわちクラスタの数。`K[i]`は`clusts[i]`のクラスタの数。
  * `r::Vector{Float64}`: パラメータ$r$の事後サンプル。
  * `p::Vector{Float64}`: パラメータ$p$の事後サンプル。
  * `K_mean`, `r_mean`, `p_mean`: それぞれの`K`、`r`、`p`の事後平均。
  * `K_variance`, `r_variance`, `p_variance`: それぞれの`K`、`r`、`p`の事後分散。
  * `K_acf::Vector{Float64}`, `r_acf::Vector{Float64}`, `p_acf::Vector{Float64}`: それぞれの`K`、`r`、`p`の自己相関関数。
  * `K_iac`, `r_iac`, および `p_iac`: それぞれの`K`、`r`、`p`の統合自己相関係数。
  * `K_ess::Float64`, `r_ess::Float64`, および `p_ess::Float64`: それぞれの`K`、`r`、`p`の有効サンプルサイズ。
  * `loglik::Vector{Float64}`: 各サンプルの対数尤度。
  * `logposterior::Vector{Float64}`: 各サンプルの対数事後に比例する関数で、比例定数は分割事前の正規化定数に等しい。
  * `splitmerge_splits`: スプリットマージステップでスプリット提案が使用されたイテレーションを示すブールベクトル。長さは`numMH * numiters`（[`MCMCOptionsList`](@ref）を参照）。
  * `splitmerge_acceptance_rate`: スプリットマージ提案の受け入れ率。
  * `r_acceptances`: メトロポリス・ヘイスティングス提案が受け入れられたイテレーション（バーニンおよび間引きされたイテレーションを含む）を示すブールベクトル。
  * `r_acceptance_rate:`: $r$のメトロポリス・ヘイスティングス受け入れ率。
  * `runtime`: すべてのイテレーションの合計実行時間。
  * `mean_iter_time`: 各イテレーションにかかる平均時間。

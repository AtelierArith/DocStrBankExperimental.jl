適応型MCMCサンプラーで、勾配情報を利用します。Livingstone et al. (2020) に基づいています。適応はAndrieu and Thoms (2008)に基づいており、セクション5のアルゴリズム4です。

```Julia
barker_mcmc(lp,
            inits::AbstractVector;
            n_iter = 100::Int,
            σ = 2.4/(length(inits)^(1/6)),
            target_acceptance_rate = 0.4,
            κ::Float64 = 0.6,
            n_iter_adaptation = Inf,
            preconditioning::Function = BarkerMCMC.precond_eigen)
```

または

```Julia
barker_mcmc(log_p::Function, ∇log_p::Function,
            inits::AbstractVector;
            n_iter = 100::Int,
            σ = 2.4/(length(inits)^(1/6)),
            target_acceptance_rate = 0.4,
            κ::Float64 = 0.6,
            n_iter_adaptation = Inf,
            preconditioning::Function = BarkerMCMC.precond_eigen)
```

### 引数

  * `lp`: `LogDensityProblems.jl`パッケージのAPIをサポートする対数密度オブジェクト
  * `log_p::Function`: （非正規化）密度の対数を返す関数
  * `∇log_p::Function`: （非正規化）密度の対数の勾配を返す関数
  * `inits::Vector`: 初期の開始値
  * `n_iter = 100`: 繰り返し回数
  * `σ = 2.4/(length(inits)^(1/6))`: 提案分布のグローバルスケール
  * `target_acceptance_rate = 0.4`: 望ましい受け入れ率
  * `κ = 0.6`: 適応速度を制御します。κ ∈ (0.5, 1)。大きな値は適応を遅くします。Livingstone et al. (2020)のセクション6.1を参照してください。
  * `n_iter_adaptation = Inf`: 適応を伴う繰り返し回数
  * `preconditioning::Function = BarkerMCMC.precond_eigen`: `BarkerMCMC.precond_eigen`または`BarkerMCMC.precond_cholesky`のいずれか。コレスキー分解を用いた前処理行列の計算は若干安価ですが、固有値分解は提案分布の適切な回転を可能にします。

### 戻り値

フィールドを持つ名前付きタプル：

  * `samples`: サンプルを含む配列
  * `log_p`: 各サンプルの`log_p`の値を含むベクター。

### 参考文献

Andrieu, C., Thoms, J., 2008. A tutorial on adaptive MCMC. Statistics and computing 18, 343–373.

Livingstone, S., Zanella, G., 2021. The Barker proposal: Combining robustness and efficiency in gradient-based MCMC. Journal of the Royal Statistical Society: Series B (Statistical Methodology). https://doi.org/10.1111/rssb.12482

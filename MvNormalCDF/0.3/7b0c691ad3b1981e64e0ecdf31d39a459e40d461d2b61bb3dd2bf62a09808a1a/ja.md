```
mvnormcdf(μ::AbstractVector, Σ::AbstractMatrix, a::AbstractVector, b::AbstractVector; m::Integer = 1000*size(Σ,1), rng = RandomDevice())
```

正定共分散行列 Σ、平均 [0,...] を持つ多変量正規確率積分を m 点の準モンテカルロアルゴリズムを使用して計算します。下限積分制限ベクトル a と上限積分制限ベクトル b を持ちます。

$$
\Phi_k(\mathbf{a},\mathbf{b},\mathbf{\Sigma} ) = \frac{1}{\sqrt{\left | \mathbf{\Sigma}  \right |{(2\pi )^k}}}\int_{a_1}^{b_1}\int_{a_2}^{b_2}\begin{align*}
 &...\end{align*} \int_{a_k}^{b_k}e^{^{-\frac{1}{2}}\mathbf{x}^t{\mathbf{\Sigma }}^{-1}\boldsymbol{\mathbf{x}}}dx_k...dx_1
$$

確率 p は誤差推定 e と共に出力されます。

# 引数

  * `μ::AbstractVector`: 平均のベクトル
  * `Σ::AbstractMatrix`: MVN分布の正定共分散行列
  * `a::AbstractVector`: 下限積分制限の列ベクトル
  * `b::AbstractVector`: 上限積分制限の列ベクトル
  * `m::Integer`:        積分点の数（デフォルトは1000*次元）
  * `rng`: 乱数生成器

# 例

```julia
Σ = [4 3 2 1; 3 5 -1 1; 2 -1 4 2; 1 1 2 5]
μ = zeros(4)
a = [-Inf; -Inf; -Inf; -Inf]
b = [1; 2; 3; 4]
m = 5000
(p,e) = mvnormcdf(μ, Σ, a, b; m=m)
#(0.605219554009911, 0.0015718064928452481)
```

結果は準モンテカルロアルゴリズムのため、実行ごとにわずかに異なる場合があります。

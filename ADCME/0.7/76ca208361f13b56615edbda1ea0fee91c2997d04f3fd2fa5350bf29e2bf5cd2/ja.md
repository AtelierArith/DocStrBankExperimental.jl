```
MCMCSimple(obs::Array{Float64, 1}, h::Function, 
σ::Float64, θ0::Array{Float64,1}, lb::Float64, ub::Float64)
```

多くの科学計算問題におけるMCMCシミュレーションのための非常にシンプルでありながら便利なインターフェースです。

  * `obs`: 観測値
  * `h`: 前方計算関数
  * `σ`: 観測データのノイズ標準偏差
  * `ub`, `lb`: 上限と下限
  * `θ0`: 初期推定

数学モデルは次の通りです。

$$
y_{obs} = h(\theta)
$$

そして、我々は厳しい制約 `lb\leq \theta \leq ub` を持っています。

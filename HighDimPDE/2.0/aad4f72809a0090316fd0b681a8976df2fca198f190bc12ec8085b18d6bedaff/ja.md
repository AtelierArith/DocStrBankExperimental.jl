```julia
NNStopping(models, opt)
```

[Deep Optimal Stopping](https://arxiv.org/pdf/1908.01602.pdf), S Becker, P Cheridito, A Jentzen3, and T Welti.

## 引数

  * `models::Vector{Flux.Chain}`: 各モデルが時間範囲 (tspan) の特定のタイムステップに対応する Flux.Chain のベクトル。ベクトルの全体の長さは `length(timesteps) - 1` である必要があります。
  * `opt`: ニューラルネットワークを最適化するために使用される最適化アルゴリズム。デフォルトは `ADAM(0.1)` です。

## 例

d = 3 # 資産の数 r = 0.05 # 金利 beta = 0.2 # ボラティリティ T = 3 # 満期 u0 = fill(90.0, d) # 初期株価 delta = 0.1 # デルタ f(du, u, p, t) = du .= (r - delta) * u # ドリフト sigma(du, u, p, t) = du .= beta * u # 拡散 tspan = (0.0, T) N = 9 # 離散化パラメータ dt = T / (N) K = 100.00 # 行使価格

# ペイオフ関数

function g(x, t)     return exp(-r * t) * (max(maximum(x) - K, 0)) end

prob = PIDEProblem(f, sigma, u0, tspan; payoff = g) models = [Chain(Dense(d + 1, 32, tanh), BatchNorm(32, tanh), Dense(32, 1, sigmoid))           for i in 1:N]

opt = Flux.Optimisers.Adam(0.01) alg = NNStopping(models, opt)

sol = solve(prob, alg, SRIW1(); dt = dt, trajectories = 1000, maxiters = 1000, verbose = true) ```

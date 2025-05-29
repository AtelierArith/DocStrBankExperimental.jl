```julia
DeepBSDE(u0,σᵀ∇u;opt=Flux.Optimise.Adam(0.1))
```

[DeepBSDEアルゴリズム](https://arxiv.org/abs/1707.02568)、J. Han、A. Jentzen、Weinan Eによる。

## 引数

  * `u0`: ソリューションの推測のためのd次元入力と1次元出力を持つFlux.jlの`Chain`。
  * `σᵀ∇u`: BSDE値の推測のためのFlux.jlの`Chain`。
  * `opt`: ニューラルネットワークを最適化するために使用される最適化アルゴリズム。デフォルトは`Flux.Optimise.Adam(0.1)`。

## 例

ブラック-ショールズ-バレンブラット方程式

```julia
d = 30 # 次元数
x0 = repeat([1.0f0, 0.5f0], div(d,2))
tspan = (0.0f0,1.0f0)
dt = 0.2
m = 30 # 軌道の数（バッチサイズ）

r = 0.05f0
sigma = 0.4f0
f(X,u,σᵀ∇u,p,t) = r * (u - sum(X.*σᵀ∇u))
g(X) = sum(X.^2)
μ_f(X,p,t) = zero(X) #ベクトル d x 1
σ_f(X,p,t) = Diagonal(sigma*X) #行列 d x d
prob = PIDEProblem(μ_f, σ_f, x0, tspan, g, f)

hls  = 10 + d #隠れ層のサイズ
opt = Flux.Optimise.Adam(0.001)
u0 = Flux.Chain(Dense(d,hls,relu),
                Dense(hls,hls,relu),
                Dense(hls,1))
σᵀ∇u = Flux.Chain(Dense(d+1,hls,relu),
                  Dense(hls,hls,relu),
                  Dense(hls,hls,relu),
                  Dense(hls,d))
pdealg = DeepBSDE(u0, σᵀ∇u, opt=opt)

solve(prob, 
    pdealg, 
    EM(), 
    verbose=true, 
    maxiters=150, 
    trajectories=m, 
    sdealg=StochasticDiffEq., 
    dt=dt, 
    pabstol = 1f-6)
```

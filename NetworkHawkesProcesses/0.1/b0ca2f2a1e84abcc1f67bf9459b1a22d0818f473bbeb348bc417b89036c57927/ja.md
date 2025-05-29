```
vb!(process::DiscreteHawkesProcess, data; kwargs...)
```

平均場変分推論を実行します。

変分分布は次の形を取ります q(λ0)q(θ)q(W)q(A)q(ω)、ここで：

  * q(λ0) = Gamma(α, β)
  * q(θ) = Dir(γ)
  * q(W) = Gamma(kappa , ν)
  * q(A) = Bern(ρ)
  * q(ω) = Mult(u)

# 引数

  * 
  * 

# キーワード引数

  * `max_steps::Int64`: 実行する最大更新回数。
  * `Δx_thresh::Float64`: ?
  * `Δq_thresh::Float64`: ?

# 戻り値

  * `res::`: 推論ルーチンの結果を含む構造体

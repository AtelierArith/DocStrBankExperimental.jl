```
mgslp(A::Matrix{Float64}; tol::Float64 = 1e-12, p::Float64 = 1.0)
```

修正グラム・シュミット法による直交化とℓᵖピボッティングアルゴリズム (MGSLp)

# 入力引数

  * `A::Matrix{Float64}`: 直交化される列ベクトルを持つ行列。

# 出力引数

  * `A::Matrix{Float64}`: ℓᵖピボッティングに基づくAの列ベクトルの直交化行列。

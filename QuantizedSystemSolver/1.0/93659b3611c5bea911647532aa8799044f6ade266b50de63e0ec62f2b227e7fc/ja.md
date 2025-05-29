```
ODEProblem(f::Function, u::Vector{Float64}, tspan::Tuple{A,B}) where{A<:Union{Float64, Int64},B<:Union{Float64, Int64}}
```

与えられた関数 `f`、初期条件 `u`、および時間範囲 `tspan` を使用して ODE 問題を作成します。

# 引数

  * `f::Function`: ODE を定義する関数。
  * `u::Vector{Float64}`: 初期条件。
  * `tspan::Tuple{Float64,Float64}`: ODE の時間範囲。

# 戻り値

  * ODE 問題。

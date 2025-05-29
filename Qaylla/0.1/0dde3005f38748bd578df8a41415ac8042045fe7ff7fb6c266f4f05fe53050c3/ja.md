```
heun(F::Function,
     a::Number,
     y_0::Number,
     b::Number,
     nh::Number)::Tuple{Vector{Float64}, Vector{Float64}}
```

`y(t)`のHeun近似を計算します。a≤t≤bのとき。

## 引数

  * `F(t,y)::Function`: `y'(t)`。
  * `a::Number`: 初期点。
  * `y_0::Number`: aにおけるyの値。
  * `b::Number`: 最終点。
  * `nh::Number`: 1≤nhの場合、nhはaとbの間の部分区間の数です。

それ以外の場合、nhはaとbの間の部分区間の長さです。

## 戻り値

  * `t_values`::Array{Float64}: [t₀,t₁...,tₙ]、ここでtᵢ=a + ih
  * `w_values`::Array{Float64}: [w₀,w₁...,wₙ]、ここでwᵢ≈yᵢ=y(tᵢ)

## 例

```jldoctest
julia> using Qaylla

julia> F(t,y)=t-y
F (generic function with 1 method)

julia> heun(F,0,2,1,5)
([0.0, 0.2, 0.4, 0.6000000000000001, 0.8, 1.0], [2.0, 1.656, 1.410645333333333, 1.2460483128888886, 1.1475648854850369, 1.1032064529170835])

julia> heun(F,0,2,1,0.2)
([0.0, 0.2, 0.4, 0.6000000000000001, 0.8, 1.0], [2.0, 1.656, 1.410645333333333, 1.2460483128888886, 1.1475648854850369, 1.1032064529170835])
```

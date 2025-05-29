```
runge_kutta_order_4(F::Function,
                    a::Number,
                    y_0::Number,
                    b::Number,
                    nh::Number)::Tuple{Vector{Float64}, Vector{Float64}}
```

`y(t)`の4次のルンゲ・クッタ近似を計算します。a≤t≤bの範囲で。

## 引数

  * `F(t,y)::Function`: `y'(t)`。
  * `a::Number`: 初期点。
  * `y_0::Number`: aにおけるyの値。
  * `b::Number`: 最終点。
  * `nh::Number`: 1≤nhの場合、nhはaとbの間の小区間の数です。

それ以外の場合、nhはaとbの間の小区間の長さです。

## 戻り値

  * `t_values`::Array{Float64}: [t₀,t₁...,tₙ], ここで tᵢ=a + ih
  * `w_values`::Array{Float64}: [w₀,w₁...,wₙ], ここで wᵢ≈yᵢ=y(tᵢ)

## 例

```jldoctest
julia> using Qaylla

julia> F(t,y)=t-y
F (generic function with 1 method)

julia> runge_kutta_order_4(F,0,2,1,5)
([0.0, 0.2, 0.4, 0.6000000000000001, 0.8, 1.0], [2.0, 1.6562000000000001, 1.4109728133333335, 1.2464504747031113, 1.1480038853219274, 1.103655714375906])

julia> runge_kutta_order_4(F,0,2,1,0.2)
([0.0, 0.2, 0.4, 0.6000000000000001, 0.8, 1.0], [2.0, 1.6562000000000001, 1.4109728133333335, 1.2464504747031113, 1.1480038853219274, 1.103655714375906])
```

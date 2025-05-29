```
runge_kutta_order_4(F::Function,
                    a::Number,
                    y_0::Number,
                    b::Number,
                    nh::Number)::Tuple{Vector{Float64}, Vector{Float64}}
```

Computes the Runge Kutta approximation of order 4 for `y(t)`, when a≤t≤b.

## Arguments

  * `F(t,y)::Function`: The `y'(t)`.
  * `a::Number`: The initial point.
  * `y_0::Number`: The y value in a.
  * `b::Number`: The final point.
  * `nh::Number`: If 1≤nh, nh is the number of subintervals beetwen a and b,

else nh is the length of the subintervals beetwen a and b.

## Return

  * `t_values`::Array{Float64}: [t₀,t₁...,tₙ], where tᵢ=a + ih
  * `w_values`::Array{Float64}: [w₀,w₁...,wₙ], where wᵢ≈yᵢ=y(tᵢ)

## Example

```jldoctest
julia> using Qaylla

julia> F(t,y)=t-y
F (generic function with 1 method)

julia> runge_kutta_order_4(F,0,2,1,5)
([0.0, 0.2, 0.4, 0.6000000000000001, 0.8, 1.0], [2.0, 1.6562000000000001, 1.4109728133333335, 1.2464504747031113, 1.1480038853219274, 1.103655714375906])

julia> runge_kutta_order_4(F,0,2,1,0.2)
([0.0, 0.2, 0.4, 0.6000000000000001, 0.8, 1.0], [2.0, 1.6562000000000001, 1.4109728133333335, 1.2464504747031113, 1.1480038853219274, 1.103655714375906])
```

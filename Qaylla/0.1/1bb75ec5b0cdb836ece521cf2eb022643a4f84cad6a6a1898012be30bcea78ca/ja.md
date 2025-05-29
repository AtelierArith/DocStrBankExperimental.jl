```
trapeze2d(F::Function,
          a::Number,
          b::Number,
          c::Number,
          d::Number,
          n::Int,
          m::Int)::Float64
```

Fの積分を平面`XY`の矩形領域で計算し、合成台形法を適用します。

## 引数

  * `F(x,y)::Function`: 積分する関数F(x,y)。
  * `a::Number`: xの領域の下限。
  * `b::Number`: xの領域の上限。
  * `c::Number`: yの領域の下限。
  * `d::Number`: yの領域の上限。
  * `n::Number`: aとbの間の小区間の数。
  * `m::Number`: cとdの間の小区間の数。

## 例

```jldoctest
julia> using Qaylla

julia> F(x,y)=x^2 + sin(y)
F (generic function with 1 method)

julia> trapeze2d(F,0,1,0,1,2,2)
0.8250805155040757

julia> trapeze2d(F,0,1,0,1,4,2)
0.7938305155040756

julia> trapeze2d(F,0,1,0,1,2,4)
0.8323009375715021

julia> trapeze2d(F,0,1,0,1,4,4)
0.8010509375715024
```

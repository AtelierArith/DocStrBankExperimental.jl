```
trapeze2d(F::Function,
          a::Number,
          b::Number,
          c::Function,
          d::Function,
          n::Int,
          m::Int)::Float64
```

平面 `XY` の矩形でない領域における F の積分を計算し、合成台形法を適用します。

## 引数

  * `F(x,y)::Function`: 積分する関数 F(x,y)。
  * `a::Number`: x の領域の下限。
  * `b::Number`: x の領域の上限。
  * `c(x)::Function`: y の領域の下限。
  * `d(x)::Function`: y の領域の上限。
  * `n::Number`: a と b の間の小区間の数。
  * `m::Number`: c(x) と d(x) の間の小区間の数。

## 例

```jldoctest
julia> using Qaylla

julia> F(x,y)=x^2 + sin(y)
F (generic function with 1 method)

julia> c(x)=x
c (generic function with 1 method)

julia> d(x)=2*x
d (generic function with 1 method)

julia> trapeze2d(F,0,1,c,d,2,2)
0.7143707767687785

julia> trapeze2d(F,0,1,c,d,4,2)
0.6526600971423198

julia> trapeze2d(F,0,1,c,d,2,4)
0.7187860972222649

julia> trapeze2d(F,0,1,c,d,4,4)
0.6563466180940812
```

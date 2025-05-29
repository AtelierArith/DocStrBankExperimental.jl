```
simpson2d(F::Function,
          a::Number,
          b::Number,
          c::Number,
          d::Number,
          n::Int,
          m::Int)::Float64
```

平面 `XY` の長方形領域における F の積分を計算し、合成シンプソン法を適用します。

## 引数

  * `F(x,y)::Function`: 積分する関数 F(x,y)。
  * `a::Number`: x の領域の下限。
  * `b::Number`: x の領域の上限。
  * `c::Number`: y の領域の下限。
  * `d::Number`: y の領域の上限。
  * `n::Number`: a と b の間の小区間の数。
  * `m::Number`: c と d の間の小区間の数。

## 例

```jldoctest
julia> using Qaylla

julia> F(x,y)=x^2 + sin(y)
F (generic function with 1 method)

julia> simpson2d(F,0,1,0,1,2,2)
0.793195523204118

julia> simpson2d(F,0,1,0,1,2,4)
0.7930410782606442

julia> simpson2d(F,0,1,0,1,4,2)
0.793195523204118

julia> simpson2d(F,0,1,0,1,4,4)
0.7930410782606443

julia> simpson2d(F,0,1,0,1,100,100)
0.7930310274907315
```

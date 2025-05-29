```
trapeze2d(F::Function,
          a::Number,
          b::Number,
          c::Number,
          d::Number,
          n::Int,
          m::Int)::Float64
```

Computes the integral of F  in a rectangular region the plain `XY`,  applying the composite trapeze method.

## Arguments

  * `F(x,y)::Function`: F(x,y) in the function to integrate.
  * `a::Number`: The lower limit of the region in x.
  * `b::Number`: The upper limit of the region in x.
  * `c::Number`: The lower limit of the region in y.
  * `d::Number`: The upper limit of the region in y.
  * `n::Number`: The number of subintervals beetwen a and b.
  * `m::Number`: The number of subintervals beetwen c and d.

## Example

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

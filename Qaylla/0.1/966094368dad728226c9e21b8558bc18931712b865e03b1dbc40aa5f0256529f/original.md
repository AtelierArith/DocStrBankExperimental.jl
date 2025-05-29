```
simpson2d(F::Function,
          a::Number,
          b::Number,
          c::Number,
          d::Number,
          n::Int,
          m::Int)::Float64
```

Computes the integral of F  in a rectangular region the plain `XY`,  applying the composite Simpson method.

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

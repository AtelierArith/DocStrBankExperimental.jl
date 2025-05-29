```
simpson2d(F::Function,
          a::Number,
          b::Number,
          c::Function,
          d::Function,
          n::Int,
          m::Int)::Float64
```

Computes the integral of F  in a not rectangular region the plain `XY`,  applying the composite Simpson method.

## Arguments

  * `F(x,y)::Function`: F(x,y) in the function to integrate.
  * `a::Number`: The lower limit of the region in x.
  * `b::Number`: The upper limit of the region in x.
  * `c(x)::Function`: The lower limit of the region in y.
  * `d(x)::Function`: The upper limit of the region in y.
  * `n::Number`: The number of subintervals beetwen a and b.
  * `m::Number`: The number of subintervals beetwen c(x) and d(x).

## Example

```jldoctest
julia> using Qaylla

julia> F(x,y)=x^2 + sin(y)
F (generic function with 1 method)

julia> c(x)=x
c (generic function with 1 method)

julia> d(x)=2*x
d (generic function with 1 method)

julia> simpson2d(F,0,1,c,d,2,2)
0.6343236523627963

julia> simpson2d(F,0,1,c,d,4,2)
0.6367323875670757

julia> simpson2d(F,0,1,c,d,2,4)
0.6342654852512393

julia> simpson2d(F,0,1,c,d,4,4)
0.6366813209795263
```

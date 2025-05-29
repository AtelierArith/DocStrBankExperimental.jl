```
trapeze2d(F::Function,
          a::Number,
          b::Number,
          c::Function,
          d::Function,
          n::Int,
          m::Int)::Float64
```

Computes the integral of F  in a not rectangular region the plain `XY`,  applying the composite trapeze method.

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

julia> trapeze2d(F,0,1,c,d,2,2)
0.7143707767687785

julia> trapeze2d(F,0,1,c,d,4,2)
0.6526600971423198

julia> trapeze2d(F,0,1,c,d,2,4)
0.7187860972222649

julia> trapeze2d(F,0,1,c,d,4,4)
0.6563466180940812
```

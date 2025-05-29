```
newton(x,y)::Function
```

Computes the Newton interpolation polynomial

## Arguments

  * `x::Vector{Number}`: The xᵢ values for i=1,2...n
  * `y::Vector{Number}`: The f(xᵢ) values for i=1,2...n

## Return

  * `p::Function`: The Newton interpolation polynomial

## Example

```jldoctest
using Qaylla

x=0:0.5:3
y=exp.(x)
p=newton(x,y)
p(2.5)

# output

12.182493960703471
```

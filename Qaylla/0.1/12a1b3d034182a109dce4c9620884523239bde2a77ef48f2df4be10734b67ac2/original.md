```
trapeze(f::Function,a::Number,b::Number,n::Int64=1)::Float64
```

Computes the integral of f applying the composite trapeze method.

## Example

```jldoctest
julia> using Qaylla

julia> f(x)=sin(x)
f (generic function with 1 method)

julia> a=0
0

julia> b=pi/2
1.5707963267948966

julia> n=4
4

julia> trapeze(f,a,b,n)
0.9871158009727754
```

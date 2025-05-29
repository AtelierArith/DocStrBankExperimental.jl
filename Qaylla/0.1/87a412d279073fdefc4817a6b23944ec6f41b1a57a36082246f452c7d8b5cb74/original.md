```
simpson(f::Function,a::Number,b::Number,n::Int64=2)::Float64
```

Computes the integral of f applying the composite Simpson method.

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

julia> simpson(f,a,b,n)
1.0001345849741938
```

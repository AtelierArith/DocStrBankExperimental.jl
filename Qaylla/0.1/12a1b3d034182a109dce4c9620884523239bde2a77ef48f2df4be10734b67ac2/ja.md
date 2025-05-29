```
trapeze(f::Function,a::Number,b::Number,n::Int64=1)::Float64
```

fの積分を合成台形法を適用して計算します。

## 例

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

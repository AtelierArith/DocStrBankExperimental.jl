```
inpaint(A)
```

`A`の要素がすべて浮動小数点数である場合（すなわち、`eltype(A) <: AbstractFloat`）、`NaN`値をインペイントします。

# 例

```jldoctest
julia> A = float((1:3)*(1:4)') ; A[1:2, 1:2] .= NaN ; A
3×4 Array{Float64,2}:
 NaN    NaN    3.0   4.0
 NaN    NaN    6.0   8.0
   3.0    6.0  9.0  12.0

julia> inpaint(A)
3×4 Array{Float64,2}:
 1.0  2.0  3.0   4.0
 2.0  4.0  6.0   8.0
 3.0  6.0  9.0  12.0
```

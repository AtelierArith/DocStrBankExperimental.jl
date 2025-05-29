```
jacobi(a,b, d::AbstractInterval)
```

[`Jacobi`](@ref) 多項式を区間 `d` にアフィンマッピングしたものです。

# 例

```jldoctest
julia> J = jacobi(1, 1, 0..1)
Jacobi(1, 1) が 0 .. 1 にアフィンマッピングされました

julia> axes(J)
(Inclusion(0 .. 1), OneToInf())

julia> J[0,:]
ℵ₀-element view(::Jacobi{Float64, Int64}, -1.0, :) with eltype Float64 with indices OneToInf():
   1.0
  -2.0
   3.0
  -4.0
   5.0
  -6.0
   7.0
  -8.0
   9.0
 -10.0
   ⋮
```

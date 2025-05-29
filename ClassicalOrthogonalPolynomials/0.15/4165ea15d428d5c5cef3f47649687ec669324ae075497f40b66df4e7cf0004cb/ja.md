```
Legendre{T=Float64}(a,b)
```

レジェンドル多項式を表す準行列で、最初の軸は区間を、2番目の軸は多項式のインデックス（1から始まる）を表します。詳細は [`legendre`](@ref)、[`legendrep`](@ref)、[`LegendreWeight`](@ref)、および [`Jacobi`](@ref) を参照してください。

# 例

```jldoctest
julia> P = Legendre()
Legendre()

julia> typeof(P) # デフォルトのeltype
Legendre{Float64}

julia> axes(P)
(Inclusion(-1.0 .. 1.0 (Chebyshev)), OneToInf())

julia> P[0,:] # x=0での多項式の値
ℵ₀-element view(::Legendre{Float64}, 0.0, :) with eltype Float64 with indices OneToInf():
  1.0
  0.0
 -0.5
 -0.0
  0.375
  0.0
 -0.3125
 -0.0
  0.2734375
  0.0
  ⋮

julia> P₀=P[:,1]; # P₀は定数の最初のレジェンドル多項式です。

julia> P₀[0],P₀[0.5]
(1.0, 1.0)
```

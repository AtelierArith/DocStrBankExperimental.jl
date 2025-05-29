```
Jacobi{T}(a,b)
Jacobi(a,b)
```

ジャコビ多項式を表す準行列で、最初の軸は区間を、2番目の軸は多項式のインデックス（1から始まる）を表します。詳細は[`jacobi`](@ref)、[`jacobip`](@ref)、および[`JacobiWeight`](@ref)を参照してください。

指定されていない場合、eltypeは浮動小数点データ型に変換されます。

# 例

```jldoctest
julia> J=Jacobi(0, 0) # eltypeはfloatに変換されます
Jacobi(0, 0)

julia> axes(J)
(Inclusion(-1.0 .. 1.0 (Chebyshev)), OneToInf())

julia> J[0,:] # x=0での多項式の値
ℵ₀-element view(::Jacobi{Float64, Int64}, 0.0, :) with eltype Float64 with indices OneToInf():
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

julia> J0=J[:,1]; # J0は定数の最初のジャコビ多項式です。

julia> J0[0],J0[0.5]
(1.0, 1.0)
```

```
nonherm(size::Ti, diag_l::Ti, diag_u::Ti, spectrum::AbstractVector{Tv}, Am::SparseMatrixCSC{Tv, Ti}, nilp::Nilpotent{Ti}) where {Tv<:Complex, Ti<:Integer}
```

ユーザー提供のニルポテント行列と行列の初期化を使用して非エルミート行列を生成します。

## 例

```julia
julia> spec=[1+im, 2, 4, 6, 7-2im, 4+3im, 7, 8, 9, 10.2-im]
10-element Vector{ComplexF64}:
  1.0 + 1.0im
  2.0 + 0.0im
  4.0 + 0.0im
  6.0 + 0.0im
  7.0 - 2.0im
  4.0 + 3.0im
  7.0 + 0.0im
  8.0 + 0.0im
  9.0 + 0.0im
 10.2 - 1.0im

julia> Am = spzeros(ComplexF64, 10, 10);
julia> initMat!(Am, -8, -2, 10; scale=0.1, sparsity=0.005)
julia> nilp=SMG2S.Nilp(4, 3, 10)
┌ Info: 与えられたニルポテント行列の次数は：
└   degree = 2
Nilpotent{Int64}(1, 10, 2,
 ⋅  ⋅  ⋅  1  ⋅  ⋅  ⋅  ⋅  ⋅  ⋅
 ⋅  ⋅  ⋅  ⋅  ⋅  ⋅  ⋅  ⋅  ⋅  ⋅
 ⋅  ⋅  ⋅  ⋅  ⋅  ⋅  ⋅  ⋅  ⋅  ⋅
 ⋅  ⋅  ⋅  ⋅  ⋅  ⋅  ⋅  ⋅  ⋅  ⋅
 ⋅  ⋅  ⋅  ⋅  ⋅  ⋅  ⋅  1  ⋅  ⋅
 ⋅  ⋅  ⋅  ⋅  ⋅  ⋅  ⋅  ⋅  ⋅  ⋅
 ⋅  ⋅  ⋅  ⋅  ⋅  ⋅  ⋅  ⋅  ⋅  1
 ⋅  ⋅  ⋅  ⋅  ⋅  ⋅  ⋅  ⋅  ⋅  ⋅
 ⋅  ⋅  ⋅  ⋅  ⋅  ⋅  ⋅  ⋅  ⋅  ⋅
 ⋅  ⋅  ⋅  ⋅  ⋅  ⋅  ⋅  ⋅  ⋅  ⋅)

julia> nonherm(10, -8, -2, spec, Am, nilp)
10×10 SparseMatrixCSC{ComplexF64, Int64} with 13 stored entries:
 1.0+1.0im      ⋅          ⋅      -2.5+0.5im      ⋅          ⋅          ⋅           ⋅          ⋅           ⋅
     ⋅      2.0+0.0im      ⋅           ⋅          ⋅          ⋅          ⋅           ⋅          ⋅           ⋅
     ⋅          ⋅      4.0+0.0im       ⋅          ⋅          ⋅          ⋅           ⋅          ⋅           ⋅
     ⋅          ⋅          ⋅       6.0+0.0im      ⋅          ⋅          ⋅           ⋅          ⋅           ⋅
     ⋅          ⋅          ⋅           ⋅      7.0-2.0im      ⋅          ⋅      -0.5-1.0im      ⋅           ⋅
     ⋅          ⋅          ⋅           ⋅          ⋅      4.0+3.0im      ⋅           ⋅          ⋅           ⋅
     ⋅          ⋅          ⋅           ⋅          ⋅          ⋅      7.0+0.0im       ⋅          ⋅      -1.6+0.5im
     ⋅          ⋅          ⋅           ⋅          ⋅          ⋅          ⋅       8.0+0.0im      ⋅           ⋅
     ⋅          ⋅          ⋅           ⋅          ⋅          ⋅          ⋅           ⋅      9.0+0.0im       ⋅
     ⋅          ⋅          ⋅           ⋅          ⋅          ⋅          ⋅           ⋅          ⋅      10.2-1.0im
```

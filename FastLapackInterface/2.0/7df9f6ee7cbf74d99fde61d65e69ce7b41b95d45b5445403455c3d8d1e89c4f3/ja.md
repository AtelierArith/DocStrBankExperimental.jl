```
GeneralizedSchurWs
```

[`LinearAlgebra.GeneralizedSchur`](https://docs.julialang.org/en/v1/stdlib/LinearAlgebra/#LinearAlgebra.GeneralizedSchur) の一般化シュア分解の表現に使用されるワークスペースで、[`LAPACK.gges!`](@ref) 関数を使用します。

# 例

```jldoctest
julia> A = [1.2 2.3
            6.2 3.3]
2×2 Matrix{Float64}:
 1.2  2.3
 6.2  3.3

julia> B = [8.2 0.3
            1.7 4.3]
2×2 Matrix{Float64}:
 8.2  0.3
 1.7  4.3

julia> ws = GeneralizedSchurWs(A)
GeneralizedSchurWs{Float64}
  work: 90-element Vector{Float64}
  αr: 2-element Vector{Float64}
  αi: 2-element Vector{Float64}
  β: 2-element Vector{Float64}
  vsl: 2×2 Matrix{Float64}
  vsr: 2×2 Matrix{Float64}
  sdim: Base.RefValue{Int64}
  bwork: 2-element Vector{Int64}
  eigen_values: 2-element Vector{ComplexF64}
  
julia> t = GeneralizedSchur(LAPACK.gges!(ws, 'V','V', A, B)...)
GeneralizedSchur{Float64, Matrix{Float64}, Vector{ComplexF64}, Vector{Float64}}
S 因子:
2×2 Matrix{Float64}:
 -1.43796  1.63843
  0.0      7.16295
T 因子:
2×2 Matrix{Float64}:
 5.06887  -4.00221
 0.0       6.85558
Q 因子:
2×2 Matrix{Float64}:
 -0.857329  0.514769
  0.514769  0.857329
Z 因子:
2×2 Matrix{Float64}:
 -0.560266  0.828313
  0.828313  0.560266
α:
2-element Vector{ComplexF64}:
 -1.4379554610733563 + 0.0im
   7.162947865097022 + 0.0im
β:
2-element Vector{Float64}:
 5.068865029631368
 6.855578082442485
```

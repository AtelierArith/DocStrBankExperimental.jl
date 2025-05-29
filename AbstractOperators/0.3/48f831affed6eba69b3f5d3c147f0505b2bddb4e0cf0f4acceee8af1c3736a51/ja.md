`IRDFT([domainType=Float64::Type,] dim_in::Tuple, d::Int, [,dims=1])`

`IRDFT(x::AbstractArray, d::Int, [,dims=1])`

複素配列 `x` に掛け算されると、次元 `dims` にわたる IDFT を返す `LinearOperator` を作成します。これはエルミート対称性を利用しています。関数 `BASE.irfft` と同様に、`d` は `div(d,2)+1 == size(x,dims)` を満たさなければなりません。

```julia
julia> A = IRDFT(Complex{Float64},(10,),19)
ℱ⁻¹  ℂ^10 -> ℝ^19 

julia> A = IRDFT((5,10,8),19,2)
ℱ⁻¹  ℂ^(5, 10, 8) -> ℝ^(5, 19, 8)

```

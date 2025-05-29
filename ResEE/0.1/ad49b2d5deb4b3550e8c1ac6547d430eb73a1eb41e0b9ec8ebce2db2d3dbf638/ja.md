```
get_entEntropy!(rho::Matrix{T}, lambdas::AbstractVector{Float64}; tol=1E-10, check::Bool=true) where T <: Union{Float64, ComplexF64}
```

エンタングルメントエントロピー Sv を取得し、エンタングルメントスペクトル `lambdas` をその場で作成します。

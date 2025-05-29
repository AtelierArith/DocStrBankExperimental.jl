```julia
FindReducedChi(Q::Vector{Float64}, Omega::Float64 , M::Model; a::Int64=3, b::Int64=3, eta::Float64=1e-2) --> ComplexF64
```

関数は、固定されたΩ=`Omega`と`Q`、および`a`と`b`によって与えられた固定の方向に沿った感受性を計算します。

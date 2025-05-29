```julia
GetBondPhase(A::Function, r1::Vector{Float64}, r2::Vector{Float64} ; n::Int64 = 100, _kwargs::Dict = Dict()) --> ComplexF64
```

与えられたゲージベクトルポテンシャル `A` を持つ格子上の2つのサイト `r1` と `r2` の間の結合におけるタイトバインディング位相を返します。位相は、結合に沿ってベクトルポテンシャルを積分することによって計算されます。

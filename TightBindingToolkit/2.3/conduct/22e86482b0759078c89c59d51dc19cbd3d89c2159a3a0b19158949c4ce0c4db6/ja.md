```julia
SpectralContribution(v::Vector{Array{Matrix{ComplexF64}}}, H::Array{Matrix{ComplexF64}, N}, omega::Float64;  spread::Float64 = 1e-3, a::Int64 = 1):: ComplexF64 where {N}
SpectralContribution(v::Vector{Array{Matrix{ComplexF64}}}, A::Array{Matrix{ComplexF64}, N};  a::Int64 = 1):: ComplexF64 where {N}
SpectralContribution(v::Vector{Array{Matrix{ComplexF64}}}, H::Array{Matrix{ComplexF64}, N}, omega1::Float64, omega2::Float64;  spread::Float64 = 1e-3, a::Int64 = 1, b::Int64 = 2):: ComplexF64 where {N}
SpectralContribution(v::Vector{Array{Matrix{ComplexF64}}}, A1::Array{Matrix{ComplexF64}, N}, A2::Array{Matrix{ComplexF64}, N} ;  a::Int64 = 1, b::Int64 = 2):: ComplexF64 where {N}
```

導電率に寄与するスペクトル関数からの寄与は、方向 `a`（および `b`）から来ています。オプションで周波数 `omega`（および `omega2`）を渡すこともできます。

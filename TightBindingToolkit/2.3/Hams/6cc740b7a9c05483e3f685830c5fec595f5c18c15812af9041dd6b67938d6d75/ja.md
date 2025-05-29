```julia
GetVelocity!(H::Hamiltonian, bz::BZ) --> Vector{Array{Matrix{ComplexF64}, T}}
```

は、各k点での速度行列のベクトルを返します。これは∂H(k)/∂k^{μ}として定義されます。

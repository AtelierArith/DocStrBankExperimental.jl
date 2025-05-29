```julia
HermitianBasis(localDim::Int64) --> Vector{Matrix{ComplexF64}}
```

Returns a vector basis of Traceless, localDim x localDim, Hermitian matrices, normalized such that $Tr(T^{a †} . T^{b}) = (1/2)δ_{ab}$, along with the identity. 

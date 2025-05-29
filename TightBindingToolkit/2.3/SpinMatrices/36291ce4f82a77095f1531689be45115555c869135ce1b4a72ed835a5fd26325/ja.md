```julia
HermitianBasis(localDim::Int64) --> Vector{Matrix{ComplexF64}}
```

トレースのない、localDim x localDim のエルミート行列のベクトル基底を返し、$Tr(T^{a †} . T^{b}) = (1/2)δ_{ab}$ となるように正規化され、単位行列も含まれます。

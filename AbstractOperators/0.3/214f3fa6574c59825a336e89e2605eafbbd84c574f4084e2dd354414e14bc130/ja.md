`codomainType(A::AbstractOperator)`

コドメインの型を返します。

```julia
julia> codomainType(DFT(10))
Complex{Float64}

julia> codomainType(vcat(Eye(Complex{Float64},(10,)),DFT(Complex{Float64},10)))
(Complex{Float64}, Complex{Float64})
```

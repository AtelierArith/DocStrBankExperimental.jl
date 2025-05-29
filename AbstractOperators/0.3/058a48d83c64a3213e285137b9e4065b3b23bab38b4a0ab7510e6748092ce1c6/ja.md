`domainType(A::AbstractOperator)`

ドメインの型を返します。

```julia
julia> domainType(DFT(10))
Float64

julia> domainType(hcat(Eye(Complex{Float64},(10,)),DFT(Complex{Float64},10)))
(Complex{Float64}, Complex{Float64})
```

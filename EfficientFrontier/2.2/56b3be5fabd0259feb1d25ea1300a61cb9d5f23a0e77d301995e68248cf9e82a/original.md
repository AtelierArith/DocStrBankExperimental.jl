```
    aEF = eFrontier(aCL::Vector{sCL{T}}, PS::Problem{T}; nS=Settings(PS)) where T
```

compute the Full Efficient Frontier by Status-Segment Method

the return aEF has the follwing structure

```
    struct sEF    #Efficient Frontier       Float64 is OK
        Ap::Matrix{Float64}     # v=a₂μ²+a₁μ+a₀, each row [a₂ a₁ a₀]
        mu::Vector{Float64}     #higher mean
        sgm::Vector{Float64}    #higher sigma
        Z::Matrix{Float64}      #weights, each corner portfolio in one row
        ic::Vector{Int}         #id of related critical line
    end
```

See also [`EfficientFrontier.ECL`](@ref), [`ePortfolio`](@ref), [`Problem`](@ref), [`Settings`](@ref)

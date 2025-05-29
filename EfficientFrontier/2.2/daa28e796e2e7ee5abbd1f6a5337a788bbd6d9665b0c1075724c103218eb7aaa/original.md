```
    struct sEF
```

Efficient Frontier, with fields:

```
        Ap::Matrix{Float64}     # v=a₂μ²+a₁μ+a₀, each row [a₂ a₁ a₀]
        mu::Vector{Float64}     #higher mean
        sgm::Vector{Float64}    #higher sigma
        Z::Matrix{Float64}      #weights, each corner portfolio in one row
        ic::Vector{Int}       #id of related critical line
```

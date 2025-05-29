```
       ces(y, p, α, σ, γ)

   Compute the vector of demands for output `y` under CES technology with a price vector `p`, 
   distribution parameters `α`, elasticity `σ` and scaling factor `γ`.

   # Examples
   ```jldoctest
   julia> ces(10, [1,2,3], [.1,.3,.6], 2.1, 2)
   3-element Vector{Float64}:
   1.5374084155938235
   3.6023084600464648
   6.591014163653714
   ```
```

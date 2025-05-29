```
hankel(σ::Series{C,M}, L1::Vector{M}, L2::Vector{M}) -> Array{C,2}
```

Hankel matrix of $σ$ with the rows indexed by the list of polynomials L1 and the columns by L2. The entries are the dot product for $σ$ of the corresponding elements in L1 and L2.

## Example

```
julia> L =[1, x1, x2, x1^2, x1*x2, x2^2]

julia> H = hankel(s,L,L)
6x6 Array{Float64,2}:
  4.0   5.0   7.0    5.0  11.0  13.0
  5.0   5.0  11.0   -1.0  17.0  23.0
  7.0  11.0  13.0   17.0  23.0  25.0
  5.0  -1.0  17.0  -31.0  23.0  41.0
 11.0  17.0  23.0   23.0  41.0  47.0
 13.0  23.0  25.0   41.0  47.0  49.0
```

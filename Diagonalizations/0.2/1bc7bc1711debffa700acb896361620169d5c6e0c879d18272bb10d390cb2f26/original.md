```julia
(1)
function genDataMatrix(t::Int, n::Int, A=nothing)

(2)
function genDataMatrix(::Type{Complex{T}},
                       t::Int, n::Int, A=○) where {T<:AbstractFloat}
```

(1) Generate a $t⋅n$ random data matrix as $XA$, where $X$ is a $t⋅n$ matrix with entries randomly drawn from a Gaussian distribution and $A$ a $n⋅n$ symmetric matrix, which, if not provided as argument `A`, will be generated with entries randomly drawn from a uniform distribution ∈[-1, 1].

(2) as (1), but $X$ is generated randomly from a complex Gaussian distribution and $A$is Hermitian (complex) which, if not provided as argument `A`, will be generated with entries randomly drawn from a uniform distribution ∈[-1-i1, 1+i1].

**Examples:**

```julia
A=genDataMatrix(100, 20) # (1), real
A=genDataMatrix(ComplexF64, 100, 20) # (2), complex
```

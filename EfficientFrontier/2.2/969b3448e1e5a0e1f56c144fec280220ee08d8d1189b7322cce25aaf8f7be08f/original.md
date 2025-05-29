```
    Problem(E::Vector{T}, V; u, d, G, g, A, b, equilibrate) where T
    Problem(E::Vector{T}, V, u; equilibrate) where T
    Problem(E::Vector{T}, V, u, d; equilibrate) where T
    Problem(E::Vector{T}, V, u, d, G, g; equilibrate) where T
    Problem(E::Vector{T}, V, u, d, G, g, A, b; equilibrate) where T
```

Setup a Portfolio Selection model: for mean vector E and variance matrix V

$$
	min     (1/2)z′Vz - L⋅z′E
	s.t.    Az  = b     ∈ R^{M}
	        Gz  ≤ g     ∈ R^{J}
	        d ≤ z ≤ u   ∈ R^{N}
$$

From L=+∞ to L=0. Default values: u = +∞, d = 0, G = [], g = [], A = ones(1,N), b = [1], and equilibrate = false

# Example

```
    using EfficientFrontier
    V = [1/100 1/80 1/100
        1/80 1/16 1/40
        1/100 1/40 1/25]    #variance matrix
    E = [109 / 100; 23 / 20; 119 / 100] #mean vector
    P = Problem(E, V)   #Default models, non-shortsale
    aCL = EfficientFrontier.ECL(P)  #compute all Critical Lines
    aEF = eFrontier(aCL, P)     #compute the Efficient Frontier
    mu = (aEF.mu[1]+aEF.mu[end])/2  #mu at the middle of Efficient Frontier
    z = ePortfolio(mu, aEF)     #weight of the efficient portfolio given mu

```

See [`Documentation for EfficientFrontier.jl`](https://github.com/PharosAbad/EfficientFrontier.jl/wiki)

See also [`EfficientFrontier.ECL`](@ref), [`eFrontier`](@ref), [`ePortfolio`](@ref)

```
ManifoldProjection(m, Q, k, τ=1, w=0, r=1000.0) <: Decomposition
```

A nonlinear noise reduction method, also known as "locally linear projections", which works by bringing a noisy signal closer to a multi-dimensional manifold that represents the deterministic dynamics of the signal. The method is method "IV" of [^Grassberger1993].

`m::Int` is the same as in [^Grassberger1993], the embedding dimension. `Q` is related with the *expected* dimension `d` of the manifold of the deterministic with approximate relation `d ≈ m-Q+1`. However, it is best t consider `Q` as an input parameter (the dimension of the set you project locally into) and you need to vary it to achieve the best performance. If given a `Vector{Int}` as `Q` the algorithm will iteratively do noise reduction to the resulting outputs (thus a vector is strongly recommended). Duplicate entries can exist in `Q`.

`k` can be either `Int` or a `SearchType` from [Neighborhood.jl](https://julianeighbors.github.io/Neighborhood.jl/stable/#Search-types-1). If `Int`, the `k` nearest neighbors are choosen as the neighborhood 𝓤 of each point. The paper contains an involved process for determining optimal `k::Int`, see eq.(5.4). `w` is just the Theiler window, while `r` is the value of the edge entries of vector R, and probably has not much impact (the rest of the entries are 1).

In the paper too big correction vectors were rescaled to the average magnitude of corrections, using as a criterion the distribution of their size. This is not implemented here (as it is not clear *exactly* what it means computationally, what is "too big"?) Contributing it is welcomed if you know how...

See also [^Schreiber1996] for an application of the same algorithm in real ECG data.

[^Schreiber1996]: Schreiber & Kaplan (1996). Nonlinear noise reduction for electrocardiograms. [Chaos, 6(1), 87–92](https://doi.org/10.1063/1.166148)

[^Grassberger1993]: Grassberger et al., (1993). On noise reduction methods for chaotic data. [Chaos 3(2), 127–141](https://doi.org/10.1063/1.165979)

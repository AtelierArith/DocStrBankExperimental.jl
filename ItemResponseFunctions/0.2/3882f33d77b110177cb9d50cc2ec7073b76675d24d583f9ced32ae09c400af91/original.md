```julia
likelihood(M, theta, betas, responses)

```

Evaluate the likelihood of an item response model `M` at `theta`, given item parameters `betas` and response pattern `responses`.

Items are assumed to be independent. Then, the likelihood function is defined as,

$L(\boldsymbol{u} | \theta, \boldsymbol{\beta}) = \prod_{j=1}^J P(Y_j = y | \theta, \boldsymbol{\beta}_j)$

See also [`loglikelihood`](@ref).

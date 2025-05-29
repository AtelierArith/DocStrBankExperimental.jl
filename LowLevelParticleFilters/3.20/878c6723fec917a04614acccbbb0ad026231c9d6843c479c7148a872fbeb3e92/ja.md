```
ll(θ) = log_likelihood_fun(filter_from_parameters(θ::Vector)::Function, priors::Vector{Distribution}, u, y, p)
ll(θ) = log_likelihood_fun(filter_from_parameters(θ::Vector)::Function, priors::Vector{Distribution}, u, y, x, p)
```

は関数 θ -> p(y|θ)p(θ) を返します。

```
polycor(X::Union{AbstractDataFrame, AbstractMatrix}; lower_tri = false)
```

Estimate polychoric correlation matrix from X.

# Arguments

  * `X` Matrix contains categorical vectors.
  * `lower_tri` logical.

# Examples

```julia

using Distributions
# Support function
function discretize(x, th)
    sum(th .< x)
end
# Gen sim data.
raw = rand(MvNormal([0, 0], [1 .5; .5 1]), 10000)'
τ1 = sort!(rand(Uniform(-2, 2), 3))
τ2 = sort!(rand(Uniform(-2, 2), 4))
obs = [discretize.(raw[:, 1], Ref(τ1)) discretize.(raw[:, 2], Ref(τ2)) ]

polycor(obs)
```

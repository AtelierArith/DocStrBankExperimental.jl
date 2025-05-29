```
info.Fxy
AMORS.objective_function(info::AMORS.Info)
AMORS.objective_function(G(x⊗y), μ, J(x), deg(J), ν, K(y), deg(K), α=1)
AMORS.objective_function(G(x⊗y), μ*J(x), deg(J), ν*K(y), deg(K), α=1)
```

yield the value of the AMORS objective function:

```
F(α*x, y/α, μ, ν) = F(x, y, μ*|α|^q, ν/|α|^r)
                  = G(x⊗y) + μ*J(x)*|α|^q + ν*K(y)/|α|^r
```

with `q = deg(J)` and `r = deg(K)` the homogeneous degrees of the functions `J(x)` and `K(y)`. All required arguments may be provided by AMORS algorithm state `info`.

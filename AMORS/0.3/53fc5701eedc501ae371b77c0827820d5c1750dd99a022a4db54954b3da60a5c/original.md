```
info = AMORS.Info(α, Gxy, μ, Jx, q, ν, Ky, r, iter, eval, status)
```

builds a structured object storing all information about AMORS algorithm state. This kind of object is returned by [`AMORS.solve`](@ref) and [`AMORS.solve!`](@ref)

The properties of the object include the arguments of the constructor:

```
info.α         # scaling factor
info.Gxy       # value of G(x⊗y)
info.μ         # value of hyper-parameter for J(x)
info.J         # value of J(x)
info.q         # homogeneous degree of J(x)
info.ν         # value of hyper-parameter for K(y)
info.Ky        # value of K(y)
info.r         # homogeneous degree of K(y)
info.autoscale # automatically takes the best scaling factor?
info.iter      # number of iterations
info.eval      # number of "evaluations"
info.status    # current status of the algorithm
```

plus some others:

```
info.αbest  # best scaling factor
info.Fxy    # value of F(α*x, y/α, μ, ν)
info.η      # effective hyper-parameter
```

where `F(x,y,μ,ν) = G(x⊗y) + μ*J(x) + ν*K(y)` is the objective function to be minimized by AMORS algorithm. Note that `info.αbest` and `info.α` may be different if autoscaling has been disabled in [`AMORS.solve`](@ref) or [`AMORS.solve!`](@ref).

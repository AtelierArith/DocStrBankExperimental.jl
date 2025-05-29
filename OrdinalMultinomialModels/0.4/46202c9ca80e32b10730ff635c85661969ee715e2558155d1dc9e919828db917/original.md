```
loglikelihood!(m, [needgrad=false], [needhess=false])
```

Evaluate the log-likelihood and optionally gradient and Hessian of ordered multinomial model.

# Positional arguments

  * `m::PolrModel`: a `PolrModel` type. Log-likelihood is evaluated based on

fields `Y`, `X`, `α`, `β`, and `link` of `m`.  

  * `needgrad::Bool=false`: evaluate gradient or not.
  * `needhess::Bool=false`: evaluate Fisher information matrix (FIM) (negative Hessian) or not.

# Output

  * `logl`: log-likelihood. If `needgrad=true`, field `m.∇` is overwritten by the

gradient (score) with respect to `(θ, β)`. If `needhess=true`, field `m.FIM` is overwritten by the Fisher information matrix (FIM), equivalent to negative Hessian,  with respect to `(θ, β)`.

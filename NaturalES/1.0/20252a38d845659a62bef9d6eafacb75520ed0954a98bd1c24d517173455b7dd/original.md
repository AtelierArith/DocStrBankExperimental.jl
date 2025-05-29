optimize(f, μ, σ, [method=sNES;options...])

minimizes the function `f` according to:

```
`f` : function to optimize
    μ::Vector -> cost::Real
`μ` : initial condition
    μ::Vector
`σ` : initial uncertainty on μ
    σ::{Real | Vector | Matrix}
`method` : xNES or sNES
    xNES = exponential evolution strategies, expensive but powerful on non separable objective
    sNES = separable evolution strategies, lightweight very powerful for separable or very high dimensional objectives
`options` :
         ημ = learning rate for μ,
         ησ = learning rate for uncertainties,
       atol = tolerance on uncertainties (default 1e-8),
    samples = number of samples used to build Natural Gradient approximation,
    iterations = upper limit on the number of iterations, default 10^4)
```

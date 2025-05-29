```
adaptive_birkhoff_extrapolation(h::Function, F::Function,
                x0::AbstractVector; rtol::Number=1e-10, Kinit = 20,
                Kmax = 100, Kstride=20, iterative::Bool=false,
                Nfactor::Integer=1, rre::Bool=true)
```

Adaptively applies `birkhoff_extrapolation` to find a good enough filter length `K`, where "good enough" is defined by the `rtol` optional argument.

Arguments:

  * `h`: The observable function (can choose the identity as a default `h = (x)->x`)
  * `F`: The symplectic map
  * `x0`: The initial point of the trajectory
  * `rtol`: Required tolerance for convergence (inexact maps often require a looser tolerance)
  * `Kinit`: The length of the initial filter
  * `Kmax`: The maximum allowed filter size
  * `Kstride`: The amount `K` increases between applications of            `birkhoff_extrapolation`
  * `iterative`: Whether to use an iterative method to solve the Hankel system              in the extrapolation step
  * `Nfactor`: How rectangular the extrapolation algorithm is. Must be >=1.
  * `rre`: Turn to true to use reduced rank extrapolation instead of minimal        polynomial extrapolation.

Outputs:

  * `c`: Linear model / filter
  * `sums`: The extrapolated value applied to each window
  * `resid`: The least squares residual
  * `xs`: A time series `x[:,n] = Fⁿ(x[:,0])`
  * `hs`: The observations `h[:,n] = h(x[:,n])`
  * `rnorm`: The norm of resid
  * `K`: The final degree of the filter
  * `history`: Returned if `iterative=true`. The history of the final LSQR iteration

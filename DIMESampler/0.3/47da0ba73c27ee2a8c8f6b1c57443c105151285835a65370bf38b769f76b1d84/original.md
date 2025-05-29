```
DIMESampler(lprobFunc::Function, init::Array, niter::Int; sigma::Float64=1e-5, gamma=nothing, aimh_prob::Float64=0.05, nsamples_proposal_dist=nothing, df_proposal_dist::Int=10, rho::Float64=.999, progress::Bool=true)
```

# Arguments

  * `lprobFunc::Function`: the likelihood function to be sampled. Expected to be vectorized.
  * `init::Array`: the initial ensemble. Used to infer the number of chains and the dimensionality of `lprobFunc`. A rule of thumb for the number of chains is :math:`nchain = 5*ndim`.
  * `niter::Int`: the number of iterations to be run.
  * `sigma::Float=1e-5`: the standard deviation of the Gaussian used to stretch the proposal vector.
  * `gamma::Float=nothing`: the mean stretch factor for the proposal vector. By default, it is $2.38 / \sqrt{2\,\mathrm{ndim}}$ as recommended by `ter Braak (2006) <http://www.stat.columbia.edu/~gelman/stuff_for_blog/cajo.pdf>`_.
  * `aimh_prob::Float=0.1`: the probability to draw a AIMH proposal.
  * `rho::Float=0.999`: the decay parameter for mean and covariance of the AIMH proposals.
  * `df_proposal_dist::Float=10`: the degrees of freedom of the multivariate t distribution used for AIMH proposals.

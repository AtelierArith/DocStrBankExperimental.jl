```
emcee(pdf, theta0s;
      niter=10^5,
      nburnin=niter÷2,
      nthin=1,
      a_scale=2.0, # step scale parameter.  Probably needn't be adjusted
      use_progress_meter=true,
      hasblob=false,
      init_blobs=init_output_vector, # initialize storage for blobs, of form (blob0, nsamples_walker) -> container
      reduce_blob!=(blobs, blob) -> push!(blobs, blob) # add one blob to blob-storage
```

The affine invariant MCMC sampler, aka MC hammer in its Python emcee implementation

Input:

  * pdf – The probability log-density function to sample.

    ```
       The pdf can also returns an arbitrary blob of something.
       `p, blob = pdf(theta)` where `theta` are the parameters.
    ```
  * theta0s – initial parameters, a Vector of length of the number of walkers.            Consider creating them with `make_theta0s(theta0, ballradius)`

Note that theta0s[1] need to support `.+`, `.*`, and `length`.

Optional key-word input:

  * niter – total number of steps to take (10^5) (==total number of log-density evaluations).
  * nburnin – total number of initial steps discarded, aka burn-in (niter/3)
  * nthin – only store every n-th sample (default=1)
  * use*progress*meter=true : whether to show a progress meter
  * hasblob=false – whether the pdf also returns a blob
  * init*blobs=init*output_vector – initialize storage for blobs of one walker, of form `(blob0, nsamples) -> container`
  * reduce_blob!=(blobs, blob) -> push!(blobs, blob) – add or reduce one blob into blob-storage (of one walker)

Output:

  * samples: of type & size `Matrix{typeof(theta0)}(niter-nburnin, nwalkers)`
  * accept_ratio: ratio of accepted to total steps
  * logdensities: the value of the log-density for each sample
  * blobs: anything else that the pdf-function returns as second argument

Notes:

  * use `squash_walkers(samples)` to concatenate all walkers-chains into one.

Reference:

  * Goodman, Jonathan, and Jonathan Weare, 2010 http://dx.doi.org/10.2140/camcos.2010.5.65
  * emcee https://github.com/dfm/emcee
  * Foreman-Mackey et al. 2013, emcee: The MCMC hammer, https://github.com/dfm/emcee

Example

```
thetas, accept_ratio, logdensities = emcee(x->-sum(x.^2), [1.0, 2, 5, 8])
```

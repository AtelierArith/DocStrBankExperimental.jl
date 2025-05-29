```
metropolis(pdf, sample_ppdf, theta0;
           niter=10^5,
           nburnin=niter÷2,
           nthin=1,
           use_progress_meter=true,
           hasblob=false, # whether the pdf also returns a blob
           init_blobs=init_output_vector, # initialize storage for blobs, of form (blob0, nsamples) -> container
           reduce_blob!=(blobs, blob) -> push!(blobs, blob) # add or reduce one blob into blob-storage
```

Metropolis sampler, the simplest MCMC method. Can only be used with symmetric proposal distributions (`ppdf`).

Input:

  * pdf – The probability log-density function to sample.

    ```
       It can also returns an arbitrary blob of
       something as second output argument.
       `p, blob = pdf(theta)` where `theta` are the parameters.
    ```
  * sample*ppdf – draws a sample for the proposal/jump distribution                `sample*ppdf(theta)`.  Needs to be symmetric:`ppdf(theta1)==ppdf(theta2)`.  Example:`theta -> c*randn() + theta`
  * theta0 – initial value of parameters (<:AbstractVector)

Optional keyword input:

  * niter – number of steps to take (10^5)
  * nburnin – number of initial steps discarded, aka burn-in (niter/3)
  * nthin – only store every n-th sample (default=1)
  * use*progress*meter=true : whether to show a progress meter
  * hasblob=false – whether the pdf also returns a blob
  * init*blobs=init*output_vector – initialize storage for blobs, of form (blob0, nsamples) -> container
  * reduce_blob!=(blobs, blob) -> push!(blobs, blob) – add or reduce one blob into blob-storage

Notes:

  * single threaded

Output:

  * samples:

      * if typeof(theta0)==Vector then Array{eltype(theta0)}(length(theta0), niter-nburnin)
      * if typeof(theta0)!=Vector then Array{typeof(theta0)}(niter-nburnin)
  * accept_ratio: ratio accepted to total steps
  * logdensities: the value of the log-density for each sample
  * blobs: anything else that the pdf-function returns as second argument

```
MCMCSolver([;sampler, parallel, nsamples, nchains; kwargs, verbose])
```

Construct an `MCMCSolver`, specifying how to invert a probabilistic backscattering model using Markov-chain Monte Carlo. By default uses the no-U-turn sampler with  acceptance rate 0.8 and collects 1000 samples. See Turing.jl documentation for more information on options for MCMC sampling.

```
 sample(L::ProjectionEnsemble;nsamples=1)
```

Sample from a projection DPP. If nsamples > 1, return a vector of nsamples realisations from the process.

If n is much larger than m, this calls the optimised accept/reject sampler instead of the regular sampler. In addition, the leverage scores are precomputed if nsamples > 1.

The optimised A/R sampler is described in  Barthelme, S, Tremblay, N, Amblard, P-O, (2022)  A Faster Sampler for Discrete Determinantal Point Processes. 

```@example
    Z = randn(150,10) #random feature matrix
    Pp = ProjectionEnsemble(Z)
    sample(Pp) #should output a vector of length 10
    sample(Pp,nsamples=5) #should output a vector of 5 realisations
```

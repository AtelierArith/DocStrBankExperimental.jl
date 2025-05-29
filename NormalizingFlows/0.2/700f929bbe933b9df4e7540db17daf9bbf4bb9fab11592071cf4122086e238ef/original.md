```
elbo(flow, logp, xs) 
elbo([rng, ]flow, logp, n_samples)
```

Compute the ELBO for a batch of samples `xs` from the reference distribution `flow.dist`.

# Arguments

  * `rng`: random number generator
  * `flow`: variational distribution to be trained. In particular  `flow = transformed(q₀, T::Bijectors.Bijector)`,  q₀ is a reference distribution that one can easily sample and compute logpdf
  * `logp`: log-pdf of the target distribution (not necessarily normalized)
  * `xs`: samples from reference dist q₀
  * `n_samples`: number of samples from reference dist q₀

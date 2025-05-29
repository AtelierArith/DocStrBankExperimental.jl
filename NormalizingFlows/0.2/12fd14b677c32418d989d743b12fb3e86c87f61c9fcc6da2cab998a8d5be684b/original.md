```
loglikelihood(rng, flow::Bijectors.TransformedDistribution, xs::AbstractVecOrMat)
```

Compute the log-likelihood for variational distribution flow at a batch of samples xs from  the target distribution p. 

# Arguments

  * `rng`: random number generator (empty argument, only needed to ensure the same signature as other variational objectives)
  * `flow`: variational distribution to be trained. In particular  "flow = transformed(q₀, T::Bijectors.Bijector)",  q₀ is a reference distribution that one can easily sample and compute logpdf
  * `xs`: samples from the target distribution p.

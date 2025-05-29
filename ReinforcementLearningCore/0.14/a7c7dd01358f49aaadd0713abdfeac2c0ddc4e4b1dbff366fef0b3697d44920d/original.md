```
SoftGaussianNetwork(;pre=identity, μ, σ, min_σ=0f0, max_σ=Inf32, squash = tanh)
```

Like `GaussianNetwork` but with a differentiable reparameterization trick. Mainly used for SAC. Returns `μ` and `σ` when called.  Create a distribution to sample from using `Normal.(μ, σ)`. `min_σ` and `max_σ` are used to clip the output from `σ`. `pre` is a shared body before the two heads of the NN. σ should be > 0.  You may enforce this using a `softplus` output activation. Actions are squashed by a tanh and a correction is applied to the logpdf.

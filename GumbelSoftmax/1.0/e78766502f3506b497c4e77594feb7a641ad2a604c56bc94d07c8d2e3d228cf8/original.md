```
sample_rao_gumbel_softmax(; probs=nothing, logits=nothing, k=1, tau=1.0, I=nothing, epsilon=1e-10)
```

Sample from the Rao-Blackwellized Gumbel-Softmax distribution. See https://arxiv.org/abs/2010.04838 for more details. The expected inputs are either `probs` or `logits`. If `logits` is not provided, it is computed as `log(probs + epsilon)` where `epsilon` is a small value to avoid numerical instability. The expected shape of `logits` is `(latent_dimension, categorial_dimension, batch_dimension)` to keep it consistent with Flux. `tau` is a temperature parameter that controls the smoothness of the distribution. `k` is the number of Monte Carlo samples.

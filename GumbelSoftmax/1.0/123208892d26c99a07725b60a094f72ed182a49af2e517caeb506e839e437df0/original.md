```
sample_gumbel_softmax(; probs = nothing, logits = nothing, tau = 0.1, hard = true, epsilon = 1e-10)
```

Sample from the Gumbel-Softmax distribution. The Gumbel-Softmax distribution is a continuous relaxation of the categorical distribution. It is defined as follows:

```
Gumbel-Softmax(logits) = softmax((logits + Gumbel(0, 1)) / tau)
```

where tau is a temperature parameter that controls the smoothness of the distribution. The expected inputs are either `probs` or `logits`. If `logits` is not provided, it is computed as `log(probs + epsilon)` where `epsilon` is a small value to avoid numerical instability. The expected shape of `logits` is `(latent_dimension, categorial_dimension, batch_dimension)` to keep it consistent with Flux. For example

```julia
logits = randn(30, 10, 64) # here we are sampling 64 batches. Each batch has 30 categorical distributions with 10 classes each.
z = sample_gumbel_softmax(logits=logits, tau=0.5)
sizeof(z) # (30, 10, 64)
```

The result one be one-hot encoded if `hard` is set to `true`. If `hard` is set to `false`, the result will be the soft output of the Softmax.

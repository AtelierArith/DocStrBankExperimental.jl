```
kl_divergence(L1::AbstractLEnsemble,L2::AbstractLEnsemble,k::Int;nsamples=100)
```

Estimate the KL divergence between two (k-)DPPs. The KL divergence is estimated by sampling from the k-DPP with L-ensemble L1 and computing the mean log-ratio of the probabilities. nsamples controls how many samples are taken.

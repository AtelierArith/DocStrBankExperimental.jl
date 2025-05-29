```
pyhf_logjointof(expected, obs, priors)
```

Return a callable Function that would calculate the joint log likelihood of likelihood and priors.

Equivalent of adding `loglikelihood` and `logprior` together.

!!! note
    The "constraint" terms are included here.


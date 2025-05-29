```
 marginal_kernel(L::AbstractLEnsemble)
```

Compute and return the marginal kernel of a DPP, K. The marginal kernel of a DPP is a (n x n) matrix which can be used to find the inclusion probabilities. For any fixed set of indices ind, the probability that ind is included in a sample from the DPP equals det(K[ind,ind]).

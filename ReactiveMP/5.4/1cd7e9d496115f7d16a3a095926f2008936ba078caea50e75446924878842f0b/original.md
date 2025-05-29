```
BinomialPolya
```

A node type representing a Binomial likelihood with linear predictor through logistic. A Normal prior on the weights is used.  The prior is augmented with a PolyaGamma distribution, which is used for modeling count data with overdispersion.  This implementation follows the PolyaGamma augmentation scheme for Bayesian inference. Can be used for Binomial regression. 

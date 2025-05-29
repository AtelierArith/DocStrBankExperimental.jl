```
MultinomialPolya
```

A node type representing a MultinomialPolya likelihood with linear predictor through softmax. A Normal prior on the weights is used.  The prior is augmented with a PolyaGamma distribution, which is used for modeling count data with overdispersion.  This implementation follows the PolyaGamma augmentation scheme for Bayesian inference. Can be used for Multinomial regression.  Uses cubature integration for the PolyaGamma augmentation scheme with a default of 21 points. Use `MultinomialPolyaMeta` to change the number of cubature points.

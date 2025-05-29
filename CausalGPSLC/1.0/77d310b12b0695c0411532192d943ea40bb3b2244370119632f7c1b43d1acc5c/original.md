```
getHyperParameters()
```

Returns default values for hyperparameters

  * `nU = 1`: Number of latent confounding variables assumed to be influencing all the instances that belong to one object. Inference will be performed over these values.
  * `nOuter = 20`: Number of posterior samples to draw.
  * `nMHInner = 5`: Number of internal Metropolis-Hastings updates to make per posterior sample.
  * `nESInner = 5`: Number of elliptical-slice sampling updates to make per posterior for latent confounders and binary treatment.
  * `nBurnIn = 5`: Number of posterior samples to discard when making predictions and estimates.
  * `stepSize = 1`: How frequently to use posterior samples (1 being every one after burnIn, higher being every `stepSize`*th*).
  * `predictionCovarianceNoise=1e-10`: Predicting with Gaussian processes requires use of covariance matrices that are Symmetric Positive Definite, and this covariance noise on the diagonal ensures these operations can be performed in a stable and consistent way.

hazard(X::UnivariateDistribution, t)

Provide the hazard fucntion of the random variable X (supposed to be a `Distributions.ContinuousUnivariateDistributions`) at point t. The default implementation is simply $vh(t) = \frac{f(t)}{S(t)}$ where $f$ and $S$ are the density and survival function of X. 

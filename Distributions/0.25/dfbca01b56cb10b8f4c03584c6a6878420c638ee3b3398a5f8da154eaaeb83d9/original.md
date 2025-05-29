```
Chernoff()
```

The *Chernoff distribution* is the distribution of the random variable

$$
\underset{t \in (-\infty,\infty)}{\arg\max} ( G(t) - t^2 ),
$$

where $G$ is standard two-sided Brownian motion.

The distribution arises as the limit distribution of various cube-root-n consistent estimators, including the isotonic regression estimator of Brunk, the isotonic density estimator of Grenander, the least median of squares estimator of Rousseeuw, and the maximum score estimator of Manski.

For theoretical results, see e.g. Kim and Pollard, Annals of Statistics, 1990.  The code for the computation of pdf and cdf is based on the algorithm described in Groeneboom and Wellner, Journal of Computational and Graphical Statistics, 2001.

```julia
cdf(Chernoff(),-x)              # For tail probabilities, use this instead of 1-cdf(Chernoff(),x)
```

```
estimatenoise!(nmrdata)
```

Estimate the rms noise level in the data and update `:noise` metadata.

If called on an `Array` of data, each item will be updated.

# Algorithm

Data are sorted into numerical order, and the highest and lowest 12.5% of data are discarded (so that 75% of the data remain). These values are then fitted to a truncated gaussian distribution via maximum likelihood analysis.

The log-likelihood function is:

$$
\log L(\mu, \sigma) = \sum_i{\log P(y_i, \mu, \sigma)}
$$

where the likelihood of an individual data point is:

$$
\log P(y,\mu,\sigma) =
    \log\frac{
        \phi\left(\frac{x-\mu}{\sigma}\right)
    }{
        \sigma \cdot \left[\Phi\left(\frac{b-\mu}{\sigma}\right) -
            \Phi\left(\frac{a-\mu}{\sigma}\right)\right]}
$$

and $\phi(x)$ and $\Phi(x)$ are the standard normal pdf and cdf functions.

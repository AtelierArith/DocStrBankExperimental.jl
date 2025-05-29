```
(model::Model)([rng, varinfo, sampler, context])
```

Sample from the `model` using the `sampler` with random number generator `rng` and the `context`, and store the sample and log joint probability in `varinfo`.

The method resets the log joint probability of `varinfo` and increases the evaluation number of `sampler`.

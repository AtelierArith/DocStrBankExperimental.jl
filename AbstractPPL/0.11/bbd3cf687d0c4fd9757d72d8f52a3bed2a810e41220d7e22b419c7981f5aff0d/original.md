```
logdensityof(model, trace)
```

Evaluate the (possibly unnormalized) density of the model specified by the probabilistic program in `model`, at specific values for the random variables given through `trace`.

`trace` can be of any supported internal trace type, or a fixed probability expression.

`logdensityof` should interact with conditioning and deconditioning in the way required by probability theory.

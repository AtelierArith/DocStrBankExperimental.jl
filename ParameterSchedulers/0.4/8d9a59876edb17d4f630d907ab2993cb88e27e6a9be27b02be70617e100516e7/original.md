```
OneCycle(nsteps, maxval;
         startval = maxval / 25,
         endval = maxval / 1f5,
         percent_start = 0.25)
```

Creates a one-cycle cosine schedule over `nsteps` steps warming up from `startval` up to `maxval` for `ceil(percent_start * nsteps)`, then back to `endval` (see [Super-Convergence: Very Fast Training of Neural Networks Using Large Learning Rates](https://arxiv.org/abs/1708.07120)).

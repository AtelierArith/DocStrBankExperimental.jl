```
infer(im, inf)
```

Run Gibbs sampling for `N` iterations. Each iteration changes all nodes. Discareds first `burn_in` samples and keeps only the `thin`-th sample. Ex, if `thin=3`, will discard the first two samples and keep the third.

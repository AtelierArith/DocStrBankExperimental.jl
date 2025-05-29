```
mean(loss, outputs, targets, weights; normalize=true)
```

Return mean of `loss` values over the iterables `outputs` and `targets`. The `weights` determine the importance of each observation. The option `normalize` divides the result by the sum of the weights.

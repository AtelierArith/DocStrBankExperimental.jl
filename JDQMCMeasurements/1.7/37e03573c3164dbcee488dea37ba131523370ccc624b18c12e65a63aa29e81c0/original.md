```
jackknife(
    g::Function,
    samples...;
    # KEYWORD ARGUMENTS
    bias_corrected = true,
    jackknife_samples = similar.(samples),
    jackknife_g = similar(samples[1])
)
```

Propagate errors through the evaluation of a function `g` given the binned `samples`, returning both the mean and error. If the keyword argument `bias = true`, then the $\mathcal{O}(1/N)$ bias is corrected. The keyword arguments `jackknife_samples` and `jackknife_g` can be passed to avoid temporary memory allocations.

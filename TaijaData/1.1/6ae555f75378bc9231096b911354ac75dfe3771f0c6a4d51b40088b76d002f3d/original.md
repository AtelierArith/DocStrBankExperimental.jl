```
load_linearly_separable(n=250; seed=data_seed)
```

Loads linearly separable synthetic data.

!!! note
    This calls the [`load_blobs`](@ref) function with specific parameters and the seed set to [`data_seed`](@ref). To ensure linear spearability and reproducibility, setting the `seed` keyword argument has no effect. For more flexibility, you can use [`load_blobs`](@ref) directly with different parameters if needed.


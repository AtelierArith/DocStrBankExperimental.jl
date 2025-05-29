Read .csv output files created by Stan's cmdstan executable and extract a (possibly nested) variable.

```julia
extract_reshape(a3d, col_names, var; nested)

```

### Required arguments

```julia
* `a3d` : Array n_samples x n_variables x n_chains
* `col_names` : Vector of names
* `var` : requested (nested) column
```

### Keyword arguments

```julia
* `nested` : If true, return nsamples x nchains matrices, else a single matrix
```

Exported

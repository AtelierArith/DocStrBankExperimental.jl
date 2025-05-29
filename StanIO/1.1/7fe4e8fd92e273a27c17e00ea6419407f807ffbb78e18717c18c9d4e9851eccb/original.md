Read .csv output files created by Stan's cmdstan executable and extract a (possibly nested) variable.

```julia
extract_reshape(csvfiles, var; nested)

```

### Required arguments

```julia
* `csvfiles` : Vector of file names
* `var` : requested (nested) column
```

### Keyword arguments

```julia
* `nested` : If true, return nsamples x nchains matrices, else a single matrix
```

Exported

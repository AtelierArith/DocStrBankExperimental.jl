Create a SampleModel and compile Stan Language Model.

```julia
SampleModel(name, model)
SampleModel(name, model, tmpdir)

```

# Extended help

### Required arguments

```julia
* `name::AbstractString`               # Name for the model
* `model::AbstractString`              # Stan model source
```

### Optional positional argument

```julia
* `tmpdir`                             # Directory where output files are stored
                                       # Default: `mktempdir()`
```

Note: On Windows I have seen issues using `tmpdir`.

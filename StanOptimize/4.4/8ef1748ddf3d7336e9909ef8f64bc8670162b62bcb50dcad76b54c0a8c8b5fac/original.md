# OptimizeModel

Create an OptimizeModel and compile Stan Language Model. 

### Required arguments

```julia
* `name::AbstractString`        : Name for the model
* `model::AbstractString`       : Stan model source
```

### Optional arguments

```julia
* `tmpdir=mktempdir()`          : Directory where output files are stored
```

# PathfinderModel

Create a PathfinderModel and compile the Stan Language Model.

```julia
PathfinderModel(name, model)
PathfinderModel(name, model, tmpdir)

```

### Required arguments

```julia
* `name::AbstractString`        : Name for the model
* `model::AbstractString`       : Stan model source
```

### Optional positional argument

```julia
* `tmpdir::AbstractString`      : Directory where output files are stored
```

Exported.

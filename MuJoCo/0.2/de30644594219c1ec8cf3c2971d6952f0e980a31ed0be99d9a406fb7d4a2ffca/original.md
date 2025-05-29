```
show_docs(obj, field::Symbol)
```

Prints the documentation for the `field` of `obj` (as in `obj.field`) to the console.

`obj` can be supplied as a type instead if no instances are available.

# Example Usage

Usage with a direct type:

```julia
julia> show_docs(Model, :nv)
Model.nv: number of degrees of freedom = dim(qvel)
```

Usage with an instance:

```julia
julia> model, data = MuJoCo.sample_model_and_data();
julia> show_docs(model, :nq)
Model.nq: number of generalized coordinates = dim(qpos)
julia> show_docs(data, :qvel)
Data.qvel: velocity (nv x 1)
```

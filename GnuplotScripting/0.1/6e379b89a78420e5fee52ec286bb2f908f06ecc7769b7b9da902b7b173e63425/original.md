```julia
register_data(gp::GnuplotScript,
              data::AbstractVecOrMat;
              copy_data::Bool=true) -> id
```

Register data and return the associated data identifier. Registered data is embedded in the plot script file. The returned `id` is used to reference registered data.

# Usage example

```julia
gp = GnuplotScript()

M = rand(10,3)

id = register_data(gp, M)

free_form(gp,"replot $id u 1:2")
free_form(gp,"replot $id u 1:3")
```

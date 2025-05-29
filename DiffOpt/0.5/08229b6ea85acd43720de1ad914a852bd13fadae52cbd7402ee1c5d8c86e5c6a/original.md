```
diff_optimizer(optimizer_constructor)
```

Creates a `DiffOpt.Optimizer`, which is an MOI layer with an internal optimizer and other utility methods. Results (primal, dual and slack values) are obtained by querying the internal optimizer instantiated using the `optimizer_constructor`. These values are required for find jacobians with respect to problem data.

One define a differentiable model by using any solver of choice. Example:

```julia
julia> import DiffOpt, HiGHS

julia> model = DiffOpt.diff_optimizer(HiGHS.Optimizer)
julia> set_attribute(model, DiffOpt.ModelConstructor, DiffOpt.QuadraticProgram.Model) # optional selection of diff method
julia> x = model.add_variable(model)
julia> model.add_constraint(model, ...)
```

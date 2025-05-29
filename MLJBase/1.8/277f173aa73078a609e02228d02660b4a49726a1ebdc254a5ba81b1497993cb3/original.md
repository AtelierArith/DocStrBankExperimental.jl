```
fitted_params(mach)
```

Return the learned parameters for a machine `mach` that has been `fit!`, for example the coefficients in a linear model.

This is a named tuple and human-readable if possible.

If `mach` is a machine for a composite model, such as a model constructed using the pipeline syntax `model1 |> model2 |> ...`, then the returned named tuple has the composite type's field names as keys. The corresponding value is the fitted parameters for the machine in the underlying learning network bound to that model. (If multiple machines share the same model, then the value is a vector.)

```julia-repl
julia> using MLJ
julia> @load LogisticClassifier pkg=MLJLinearModels
julia> X, y = @load_crabs;
julia> pipe = Standardizer() |> LogisticClassifier();
julia> mach = machine(pipe, X, y) |> fit!;

julia> fitted_params(mach).logistic_classifier
(classes = CategoricalArrays.CategoricalValue{String,UInt32}["B", "O"],
 coefs = Pair{Symbol,Float64}[:FL => 3.7095037897680405, :RW => 0.1135739140854546, :CL => -1.6036892745322038, :CW => -4.415667573486482, :BD => 3.238476051092471],
 intercept = 0.0883301599726305,)
```

See also [`report`](@ref)

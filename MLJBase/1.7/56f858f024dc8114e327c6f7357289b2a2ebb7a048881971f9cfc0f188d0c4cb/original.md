```
report(mach)
```

Return the report for a machine `mach` that has been `fit!`, for example the coefficients in a linear model.

This is a named tuple and human-readable if possible.

If `mach` is a machine for a composite model, such as a model constructed using the pipeline syntax `model1 |> model2 |> ...`, then the returned named tuple has the composite type's field names as keys. The corresponding value is the report for the machine in the underlying learning network bound to that model. (If multiple machines share the same model, then the value is a vector.)

```julia-repl
julia> using MLJ
julia> @load LinearBinaryClassifier pkg=GLM
julia> X, y = @load_crabs;
julia> pipe = Standardizer() |> LinearBinaryClassifier();
julia> mach = machine(pipe, X, y) |> fit!;

julia> report(mach).linear_binary_classifier
(deviance = 3.8893386087844543e-7,
 dof_residual = 195.0,
 stderror = [18954.83496713119, 6502.845740757159, 48484.240246060406, 34971.131004997274, 20654.82322484894, 2111.1294584763386],
 vcov = [3.592857686311793e8 9.122732393971942e6 … -8.454645589364915e7 5.38856837634321e6; 9.122732393971942e6 4.228700272808351e7 … -4.978433790526467e7 -8.442545425533723e6; … ; -8.454645589364915e7 -4.978433790526467e7 … 4.2662172244975924e8 2.1799125705781363e7; 5.38856837634321e6 -8.442545425533723e6 … 2.1799125705781363e7 4.456867590446599e6],)

```

See also [`fitted_params`](@ref)

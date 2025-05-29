```
@add_target!(prob, method, target, weight, label)
```

Construct a target from a method signature provided in `method.`  The method signature *must* have keyword arugment `geometry = geometry_key`, where `geometry_key` is the identifier returned by `@add_derived_geometry`.

Example:

```julia-repl
julia> using MPI, VMEC, StellaratorOptimization

julia> prob = StellOpt.Problem{Float64}();

julia> vmec_wrapper = EquilibriumWrapper(input_dictionary);

julia> add_equilibrium_wrapper!(prob, vmec_wrapper);

julia> vmec_surface = @add_derived_geometry!(prob, VmecSurface(0.5, equilibrium = vmec_wrapper));

julia> @add_target!(prob, VMEC.quasisymmetry_deviation(1, 4, 16, 16, geometry = vmec_surface), 0.0, 1.0, "qs(0.5)");
```

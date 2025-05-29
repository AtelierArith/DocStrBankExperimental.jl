```
@add_derived_geometry!(prob, method)
```

Construct a derived geometry expression from a method signature provided in  `method.`  The method signature *must* have keyword arugment  `equilibrium = eq_wrapper`, where `eq_wrapper` is a previously  defined `EquilibriumWrapper` variable that has been added to  the optimization problem `prob` through `add_equilibrium_wrapper!`. The derived geometry expression is added to both the `prob.derived_geometries` dictionary and the corresponding `eq_wrapper.derived_geometries` dictionary.  The returned value is the hash of the `method` expression that is used as key value for the `derived_geometries` dictionaries.

See also: [`add_equilibrium_wrapper!`](@ref)

Example: ```julia-repl julia> using MPI, VMEC, StellaratorOptimization

julia> prob = StellOpt.Problem{Float64}();

julia> vmec*wrapper = EquilibriumWrapper(input*dictionary);

julia> add*equilibrium*wrapper!(prob, vmec_wrapper);

julia> vmec*surface = @add*derived*geometry!(prob, VmecSurface(0.5, equilibrium = vmec*wrapper));

julia> (typeof(vmec*surface) <: UInt, haskey(prob.derived*geometries, vmec_surface)) (true, true)

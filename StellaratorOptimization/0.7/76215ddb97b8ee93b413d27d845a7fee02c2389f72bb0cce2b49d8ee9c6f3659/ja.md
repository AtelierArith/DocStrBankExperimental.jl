```
@add_target!(prob, method, target, weight, label)
```

`method`で提供されたメソッドシグネチャからターゲットを構築します。メソッドシグネチャにはキーワード引数`geometry = geometry_key`が*必須*であり、`geometry_key`は`@add_derived_geometry`によって返される識別子です。

例:

```julia-repl
julia> using MPI, VMEC, StellaratorOptimization

julia> prob = StellOpt.Problem{Float64}();

julia> vmec_wrapper = EquilibriumWrapper(input_dictionary);

julia> add_equilibrium_wrapper!(prob, vmec_wrapper);

julia> vmec_surface = @add_derived_geometry!(prob, VmecSurface(0.5, equilibrium = vmec_wrapper));

julia> @add_target!(prob, VMEC.quasisymmetry_deviation(1, 4, 16, 16, geometry = vmec_surface), 0.0, 1.0, "qs(0.5)");
```

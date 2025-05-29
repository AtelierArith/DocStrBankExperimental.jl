```
@add_derived_geometry!(prob, method)
```

`method`で提供されたメソッドシグネチャから派生幾何学表現を構築します。メソッドシグネチャには、キーワード引数 `equilibrium = eq_wrapper` が必要であり、ここで `eq_wrapper` は、`add_equilibrium_wrapper!` を通じて最適化問題 `prob` に追加された以前に定義された `EquilibriumWrapper` 変数です。派生幾何学表現は、`prob.derived_geometries` 辞書と対応する `eq_wrapper.derived_geometries` 辞書の両方に追加されます。返される値は、`derived_geometries` 辞書のキー値として使用される `method` 表現のハッシュです。

参照: [`add_equilibrium_wrapper!`](@ref)

例: ```julia-repl julia> using MPI, VMEC, StellaratorOptimization

julia> prob = StellOpt.Problem{Float64}();

julia> vmec*wrapper = EquilibriumWrapper(input*dictionary);

julia> add*equilibrium*wrapper!(prob, vmec_wrapper);

julia> vmec*surface = @add*derived*geometry!(prob, VmecSurface(0.5, equilibrium = vmec*wrapper));

julia> (typeof(vmec*surface) <: UInt, haskey(prob.derived*geometries, vmec_surface)) (true, true) ```

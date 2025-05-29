```julia
ImplicitDiscreteFunctionExpr{iip}(sys::ImplicitDiscreteSystem, dvs = states(sys),
                                  ps = parameters(sys);
                                  version = nothing,
                                  kwargs...) where {iip}
```

[`ImplicitDiscreteSystem`](@ref)から`ImplicitDiscreteFunction`のためのJulia式を作成します。引数`dvs`と`ps`は、それぞれ従属変数とパラメータベクトルの順序を設定するために使用されます。

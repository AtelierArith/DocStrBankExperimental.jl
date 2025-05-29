```julia
DiscreteFunctionExpr{iip}(sys::DiscreteSystem, dvs = states(sys),
                          ps = parameters(sys);
                          version = nothing,
                          kwargs...) where {iip}
```

[`DiscreteSystem`](@ref)から`DiscreteFunction`のためのJulia式を作成します。引数`dvs`と`ps`は、それぞれ従属変数とパラメータベクトルの順序を設定するために使用されます。

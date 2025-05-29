```julia
SciMLBase.DiscreteFunction{iip}(sys::DiscreteSystem,
                            dvs = unknowns(sys),
                            ps = parameters(sys);
                            kwargs...) where {iip}
```

[`DiscreteSystem`](@ref)から`DiscreteFunction`を作成します。引数`dvs`と`ps`は、それぞれ従属変数とパラメータベクトルの順序を設定するために使用されます。

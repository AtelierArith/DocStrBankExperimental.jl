```julia
couple(systems...) -> EarthSciMLBase.CoupledSystem

```

複数のModelingToolkitシステムを一緒に結合します。

このシステムに引数として渡されるシステムは、`ModelingToolkit.AbstractSystem`、[`CoupledSystem`](@ref)、[`DomainInfo`](@ref)、またはメソッド`couple(::CoupledSystem, ::T)::CoupledSystem`またはメソッド`couple(::T, ::CoupledSystem)::CoupledSystem`が定義されている任意の型`T`であることができます。

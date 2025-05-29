```
build_constraint(_error::Function, Q::Symmetric{V, M},
                 ::PSDCone) where {V <: AbstractJuMPScalar,
                                   M <: AbstractMatrix{V}}
```

`Q`が半正定値であることを制約する[`SymmetricMatrixShape`](@ref)の形状の`VectorConstraint`を返します。

この関数は、次のように[`@constraint`](@ref)マクロによって使用されます：

```julia
@constraint(model, Symmetric(Q) in PSDCone())
```

上記の形式は通常、`Q`のエントリがアフィンまたは二次式である場合に使用されますが、エントリが変数である場合にも使用して半正定値制約の参照を取得できます。例えば、

```julia
@variable model Q[1:2,1:2] Symmetric
# `Q`の型は`Symmetric{VariableRef, Matrix{VariableRef}}`です
var_psd = @constraint model Q in PSDCone()
# `var_psd`変数には制約への参照が含まれています
```

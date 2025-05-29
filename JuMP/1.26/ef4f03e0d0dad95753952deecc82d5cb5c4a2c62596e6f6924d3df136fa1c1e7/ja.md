```
set_attributes(
    destination::Union{
        GenericModel,
        MOI.OptimizerWithAttributes,
        GenericVariableRef,
        ConstraintRef,
    },
    pairs::Pair...,
)
```

与えられた `attribute => value` ペアのリストに対して、各ペアに対して `set_attribute(destination, attribute, value)` を呼び出します。

参照: [`set_attribute`](@ref), [`get_attribute`](@ref).

## 例

```jldoctest
julia> import Ipopt

julia> model = Model(Ipopt.Optimizer);

julia> set_attributes(model, "tol" => 1e-4, "max_iter" => 100)
```

は次のように等価です:

```jldoctest
julia> import Ipopt

julia> model = Model(Ipopt.Optimizer);

julia> set_attribute(model, "tol", 1e-4)

julia> set_attribute(model, "max_iter", 100)
```

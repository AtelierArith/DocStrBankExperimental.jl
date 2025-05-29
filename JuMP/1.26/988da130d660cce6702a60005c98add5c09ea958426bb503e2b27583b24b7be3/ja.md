```
set_optimizer_attributes(
    model::Union{GenericModel,MOI.OptimizerWithAttributes},
    pairs::Pair...,
)
```

`attribute => value` ペアのリストを与えると、各ペアに対して `set_optimizer_attribute(model, attribute, value)` を呼び出します。

!!! compat
    このメソッドは JuMP のすべての v1.X リリースに残りますが、将来の v2.0 リリースで削除される可能性があります。代わりに [`set_attributes`](@ref) の使用を推奨します。


参照: [`set_optimizer_attribute`](@ref), [`get_optimizer_attribute`](@ref).

## 例

```jldoctest
julia> import Ipopt

julia> model = Model(Ipopt.Optimizer);

julia> set_optimizer_attributes(model, "tol" => 1e-4, "max_iter" => 100)
```

は次のように等価です:

```jldoctest
julia> import Ipopt

julia> model = Model(Ipopt.Optimizer);

julia> set_optimizer_attribute(model, "tol", 1e-4)

julia> set_optimizer_attribute(model, "max_iter", 100)
```

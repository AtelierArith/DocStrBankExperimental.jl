```
disjunction(
    model::JuMP.AbstractModel, 
    disjunct_indicators::Vector{LogicalVariableRef},
    [nested_tag::Disjunct],
    [name::String = ""];
    [exactly1::Bool = true]
)
```

Create a disjunction comprised of disjuncts with indicator variables `disjunct_indicators`  and add it to `model`. For nested disjunctions, the `nested_tag` is required to indicate  which disjunct it will be part of in the parent disjunction. By default, `exactly1` adds  a constraint of the form `@constraint(model, disjunct_indicators in Exactly(1))` only  allowing one of the disjuncts to be selected; this is required for certain reformulations like  [`Hull`](@ref). For nested disjunctions, `exactly1` creates a constraint of the form `@constraint(model, disjunct_indicators in Exactly(nested_tag.indicator))`.  To conveniently generate many disjunctions at once, see [`@disjunction`](@ref)  and [`@disjunctions`](@ref).

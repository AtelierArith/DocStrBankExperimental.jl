```
add_parameter(model::InfiniteModel, p::IndependentParameter,
              [name::String = ""])::GeneralVariableRef
```

`p`を`model`に追加することで関連付けられた[`GeneralVariableRef`](@ref)を返します。これは、`JuMP.add_variable`に似た方法でモデルにパラメータを追加します。これは、[`@infinite_parameter`](@ref)を使用してパラメータを追加するために使用されます。`p`を構築するには、[`build_parameter`](@ref build_parameter(::Function, ::InfiniteScalarDomain))を使用する必要があります。

**例**

```julia-repl
julia> p = build_parameter(error, IntervalDomain(0, 3), supports = Vector(0:3));

julia> param_ref = add_parameter(model, p, "name")
name
```

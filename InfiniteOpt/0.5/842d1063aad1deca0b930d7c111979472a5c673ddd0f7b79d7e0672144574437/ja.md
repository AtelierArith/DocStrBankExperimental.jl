```
add_parameter(model::InfiniteModel, p::FiniteParameter,
              [name::String = ""])::GeneralVariableRef
```

`p` に関連付けられた [`GeneralVariableRef`](@ref) を返し、これは `model` に追加されます。これは `JuMP.add_variable` に似た方法でモデルにパラメータを追加します。これは [`@finite_parameter`](@ref) を使用してパラメータを追加するためのものです。`p` を構築するには [`build_parameter`](@ref build_parameter(::Function, ::Real)) を使用する必要があります。

**例**

```julia-repl
julia> p = build_parameter(error, 42);

julia> param_ref = add_parameter(model, p, "name")
name
```

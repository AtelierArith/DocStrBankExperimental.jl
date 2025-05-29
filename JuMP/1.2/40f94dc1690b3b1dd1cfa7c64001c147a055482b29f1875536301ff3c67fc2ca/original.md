```
operator_to_set(_error::Function, ::Val{sense_symbol})
```

Converts a sense symbol to a set `set` such that `@constraint(model, func sense_symbol 0)` is equivalent to `@constraint(model, func in set)` for any `func::AbstractJuMPScalar`.

## Example

Once a custom set is defined you can directly create a JuMP constraint with it:

```jldoctest operator_to_set; setup = :(using JuMP)
julia> struct CustomSet{T} <: MOI.AbstractScalarSet
           value::T
       end

julia> Base.copy(x::CustomSet) = CustomSet(x.value)

julia> model = Model();

julia> @variable(model, x)
x

julia> cref = @constraint(model, x in CustomSet(1.0))
x ∈ CustomSet{Float64}(1.0)
```

However, there might be an appropriate sign that could be used in order to provide a more convenient syntax:

```jldoctest operator_to_set
julia> JuMP.operator_to_set(::Function, ::Val{:⊰}) = CustomSet(0.0)

julia> MOIU.shift_constant(set::CustomSet, value) = CustomSet(set.value + value)

julia> cref = @constraint(model, x ⊰ 1)
x ∈ CustomSet{Float64}(1.0)
```

Note that the whole function is first moved to the right-hand side, then the sign is transformed into a set with zero constant and finally the constant is moved to the set with `MOIU.shift_constant`.

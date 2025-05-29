```
prefix(model::Model, x::VarName)
prefix(model::Model, x::Val{sym})
prefix(model::Model, x::Any)
```

Return `model` but with all random variables prefixed by `x`, where `x` is either:

  * a `VarName` (e.g. `@varname(a)`),
  * a `Val{sym}` (e.g. `Val(:a)`), or
  * for any other type, `x` is converted to a Symbol and then to a `VarName`. Note that this will introduce runtime overheads so is not recommended unless absolutely necessary.

# Examples

```jldoctest
julia> using DynamicPPL: prefix

julia> @model demo() = x ~ Dirac(1)
demo (generic function with 2 methods)

julia> rand(prefix(demo(), @varname(my_prefix)))
(var"my_prefix.x" = 1,)

julia> rand(prefix(demo(), Val(:my_prefix)))
(var"my_prefix.x" = 1,)
```

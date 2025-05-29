```
mutable struct JLKwStruct <: JLExpr
JLKwStruct(;kw...)
```

Type describes a Julia struct that allows keyword definition of defaults. This syntax is similar to [`JLStruct`](@ref) except the the fields are of type [`JLKwField`](@ref).

# Fields and Keyword Arguments

All the following fields are valid as keyword arguments `kw` in the constructor, and can be access via `<object>.<field>`.

The only required keyword argument for the constructor is `name`, the rest are all optional.

  * `name::Symbol`: name of the struct, this is the only required keyword argument.
  * `typealias::String`: an alias of the [`JLKwStruct`](@ref),   see also the `@option` macro in [Configurations.jl](https://github.com/Roger-luo/Configurations.jl).
  * `ismutable::Bool`: if the struct definition is mutable.
  * `typevars::Vector{Any}`: type variables of the struct, should be `Symbol` or `Expr`.
  * `supertype`: supertype of the struct definition.
  * `fields::Vector{JLField}`: field definitions of the struct, should be a [`JLField`](@ref).
  * `constructors::Vector{JLFunction}`: constructors definitions of the struct, should be [`JLFunction`](@ref).
  * `line::LineNumberNode`: a `LineNumberNode` to indicate the definition position for error report etc.
  * `doc::String`: documentation string of the struct.
  * `misc`: other things that happens inside the struct body, by definition this will   just fall through and is equivalent to eval them outside the struct body.

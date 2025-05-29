```
mutable struct JLStruct <: JLExpr
```

Type describes a Julia struct.

```
JLStruct(;kw...)
```

Create a `JLStruct` instance.

# Available Fields and Keyword Arguments

All the following fields are valid as keyword arguments `kw` in the constructor, and can be access via `<object>.<field>`.

The only required keyword argument for the constructor is `name`, the rest are all optional.

  * `name::Symbol`: name of the struct, this is the only required keyword argument.
  * `ismutable::Bool`: if the struct definition is mutable.
  * `typevars::Vector{Any}`: type variables of the struct, should be `Symbol` or `Expr`.
  * `supertype`: supertype of the struct definition.
  * `fields::Vector{JLField}`: field definitions of the struct, should be a [`JLField`](@ref).
  * `constructors::Vector{JLFunction}`: constructors definitions of the struct, should be [`JLFunction`](@ref).
  * `line::LineNumberNode`: a `LineNumberNode` to indicate the definition position for error report etc.
  * `doc::String`: documentation string of the struct.
  * `misc`: other things that happens inside the struct body, by definition this will   just fall through and is equivalent to eval them outside the struct body.

# Example

Construct a Julia struct.

```julia
julia> JLStruct(;name=:Foo, typevars=[:T], fields=[JLField(;name=:x, type=Int)])
struct Foo{T}
    x::Int64
end
```

Decompose a Julia struct expression

```julia
julia> ex = :(struct Foo{T}
           x::Int64
       end)
:(struct Foo{T}
      #= REPL[31]:2 =#
      x::Int64
  end)

julia> jl = JLStruct(ex)
struct Foo{T}
    #= REPL[31]:2 =#
    x::Int64
end
```

Generate a Julia struct expression

```julia
julia> codegen_ast(jl)
:(struct Foo{T}
      #= REPL[31]:2 =#
      x::Int64
  end)
```

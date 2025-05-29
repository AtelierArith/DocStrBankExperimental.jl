```
JLIfElse <: JLExpr
JLIfElse(;kw...)
```

`JLIfElse` describes a Julia `if ... elseif ... else ... end` expression. It allows one to easily construct such expression by inserting condition and code block via a map.

# Fields and Keyword Arguments

All the following fields are valid as keyword arguments `kw` in the constructor, and can be access via `<object>.<field>`.

  * `conds::Vector{Any}`: expression for the conditions.
  * `stmts::Vector{Any}`: expression for the statements for corresponding condition.
  * `otherwise`: the `else` body.

# Example

### Construct JLIfElse object

One can construct an `ifelse` as following

```julia
julia> jl = JLIfElse()
nothing

julia> jl[:(foo(x))] = :(x = 1 + 1)
:(x = 1 + 1)

julia> jl[:(goo(x))] = :(y = 1 + 2)
:(y = 1 + 2)

julia> jl.otherwise = :(error("abc"))
:(error("abc"))

julia> jl
if foo(x)
    x = 1 + 1
elseif goo(x)
    y = 1 + 2
else
    error("abc")
end
```

### Generate the Julia `Expr` object

to generate the corresponding `Expr` object, one can call [`codegen_ast`](@ref).

```julia
julia> codegen_ast(jl)
:(if foo(x)
      x = 1 + 1
  elseif goo(x)
      y = 1 + 2
  else
      error("abc")
  end)
```

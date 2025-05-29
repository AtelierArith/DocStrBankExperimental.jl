```
mutable struct JLFunction <: JLExpr
JLFunction(;kw...)
```

Type describes a Julia function declaration expression.

# Fields and Keyword Arguments

All the following fields are valid as keyword arguments `kw` in the constructor, and can be access via `<object>.<field>`.

The only required keyword argument for the constructor is `name`, the rest are all optional.

  * `head`: optional, function head, can be `:function`, `:(=)` or `:(->)`.
  * `name`: optional, function name, can has type `Nothing`, `Symbol` or `Expr`, default is `nothing`.
  * `args`: optional, function arguments, a list of `Expr` or `Symbol`.
  * `kwargs`: optional, function keyword arguments, a list of `Expr(:kw, name, default)`.
  * `rettype`: optional, the explicit return type of a function,   can be a `Type`, `Symbol`, `Expr` or just `nothing`, default is `nothing`.
  * `generated`: optional, if this is a generated function.
  * `whereparams`: optional, type variables, can be a list of `Type`,   `Expr` or `nothing`, default is `nothing`.
  * `body`: optional, function body, an `Expr`, default is `Expr(:block)`.
  * `line::LineNumberNode`: a `LineNumberNode` to indicate the line information.
  * `doc::String`: the docstring of this definition.

# Example

Construct a function expression

```julia
julia> JLFunction(;name=:foo, args=[:(x::T)], body= quote 1+1 end, head=:function, whereparams=[:T])
function foo(x::T) where {T}
    #= REPL[25]:1 =#    
    1 + 1    
end
```

Decompose a function expression

```julia
julia> ex = :(function foo(x::T) where {T}
           #= REPL[25]:1 =#    
           1 + 1    
       end)
:(function foo(x::T) where T
      #= REPL[26]:1 =#
      #= REPL[26]:3 =#
      1 + 1
  end)

julia> jl = JLFunction(ex)
function foo(x::T) where {T}
    #= REPL[26]:1 =#    
    #= REPL[26]:3 =#    
    1 + 1    
end
```

Generate `Expr` from `JLFunction`

```julia
julia> codegen_ast(jl)
:(function foo(x::T) where T
      #= REPL[26]:1 =#
      #= REPL[26]:3 =#
      1 + 1
  end)
```

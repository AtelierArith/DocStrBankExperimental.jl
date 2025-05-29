```
ReplaceSymbols(expr::Expr, to_replace::Set{Symbol})

ReplaceSymbols(expr::Expr, to_replace::Symbol...)
```

Functional form of `replace_symbols`, i.e., given a set of `Symbol`s `x_old` in `to_replace`, 

this type acts as a function of the form `(x_old1 => x_new1, ..., x_oldk => x_newk) -> Expr`, where each instance of `x_oldj` in `expr` is replaced with `x_newj`, applied recursively. 

# Examples

```julia-repl
julia> f = ReplaceSymbols(:(g(_)::T), :_);

julia> f(:_ => :x)
:(g(x)::T)
```

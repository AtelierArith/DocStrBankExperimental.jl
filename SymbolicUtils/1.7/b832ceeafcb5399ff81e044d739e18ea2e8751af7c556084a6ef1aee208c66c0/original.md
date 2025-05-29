```
@syms <lhs_expr>[::T1] <lhs_expr>[::T2]...
```

For instance:

```
@syms foo::Real bar baz(x, y::Real)::Complex
```

Create one or more variables. `<lhs_expr>` can be just a symbol in which case it will be the name of the variable, or a function call in which case a function-like variable which has the same name as the function being called. The Sym type, or in the case of a function-like Sym, the output type of calling the function can be set using the `::T` syntax.

# Examples:

  * `@syms foo bar::Real baz::Int` will create

variable `foo` of symtype `Number` (the default), `bar` of symtype `Real` and `baz` of symtype `Int`

  * `@syms f(x) g(y::Real, x)::Int h(a::Int, f(b))` creates 1-arg `f` 2-arg `g`

and 2 arg `h`. The second argument to `h` must be a one argument function-like variable. So, `h(1, g)` will fail and `h(1, f)` will work.

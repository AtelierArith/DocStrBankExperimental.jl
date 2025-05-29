```
toexpr(ex, [st,])
```

Convert a symbolic expression into an `Expr`, suitable to be passed into `eval`.

For example,

```julia
julia> @syms a b
(a, b)

julia> toexpr(a+b)
:((+)(a, b))

julia> toexpr(a+b) |> dump
Expr
  head: Symbol call
  args: Array{Any}((3,))
    1: + (function of type typeof(+))
    2: Symbol a
    3: Symbol b
```

Note that the function is an actual function object.

For more complex expressions, see other code-related combinators,

Namely `Assignment`, `Let`, `Func`, `SetArray`, `MakeArray`, `MakeSparseArray` and `MakeTuple`.

To make your own type convertible to Expr using `toexpr` define `toexpr(x, st)` and forward the state `st` in internal calls to `toexpr`. `st` is state used to know when to leave something like `y(t)` as it is or when to make it `var"y(t)"`. E.g. when `y(t)` is itself the argument of a function rather than `y`.

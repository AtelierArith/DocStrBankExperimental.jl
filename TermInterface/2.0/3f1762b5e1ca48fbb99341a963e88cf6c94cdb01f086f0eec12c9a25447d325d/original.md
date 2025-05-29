```
iscall(x)
```

Returns `true` if `x` is a function call expression. If true, `operation(x)`, `arguments(x)` must also be defined for `x`.

If `iscall(x)` is true, then also `isexpr(x)` *must* be true. The other way around is not true. (A function call is always an expression node, but not every expression tree represents a function call).

This means that, `head(x)` and `children(x)` must be defined. Together with `operation(x)` and `arguments(x)`. 

## Examples

In a functional language, all expression trees are function calls (e.g. SymbolicUtils.jl). Let's say that you have an hybrid array and functional language. `iscall` on the expression `v[i]` is `false`, and `iscall` on expression `f(x)` is `true`, but both of them are nested expressions, and `isexpr` is `true` on both.

The same goes for Julia `Expr`. An `Expr(:block, ...)` is *not a function call* and has no `operation` and `arguments`, but has a `head` and `children`.

The distinction between `head`/`children` and `operation`/`arguments` is needed  when dealing with languages that are *not representing function call operations as their head*. The main example is  `Expr(:call, :f, :x)`: it has both a `head` and an `operation`, which are respectively `:call` and `:f`.

In other symbolic expression languages, such as SymbolicUtils.jl, the `head` of a node  can correspond to `operation` and `children` can correspond to `arguments`.

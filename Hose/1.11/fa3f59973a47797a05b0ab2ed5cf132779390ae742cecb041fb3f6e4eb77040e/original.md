```julia
    @hose(expression)
```

The `@hose` macro processes its argument so that you pipe the left hand side (LHS) into functions of several arguments, macros, blocks, just index the LHS etc. The placeholder symbol for the LHS on the RHS is the underscore (`_`).

Examples:

```julia
    @hose a |> b(x, _) # produces b(x, a)
    @hose a |> _[b] # produces a[b]
    @hose a |> @testmacro _ b # equivalent of @testmacro(a, b)
```

Also behaves like [Lazy.jl](https://github.com/MikeInnes/Lazy.jl) `@>` macro:

```julia
    @hose a |> b(x) # produces b(a, x)
    @hose a |> @testmacro # produces equivalent of @testmacro(a)
```

Standard piping works as well. For other examples see `test/runtests.jl`.

```
@nospecs def
```

Adds `@nospecialize` annotation to non-annotated arguments of `def`.

```julia
(Core.Compiler) julia> @macroexpand @nospecs function tfunc(𝕃::AbstractLattice, x, y::Bool, zs...)
                           x, ys
                       end
:(function tfunc($(Expr(:meta, :specialize, :(𝕃::AbstractLattice))), x, y::Bool, zs...)
      #= REPL[3]:1 =#
      $(Expr(:meta, :nospecialize, :x, :zs))
      #= REPL[3]:2 =#
      (x, ys)
  end)
```

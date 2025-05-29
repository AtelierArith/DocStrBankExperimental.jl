```
@nospecs def
```

`def`の非注釈引数に`@nospecialize`アノテーションを追加します。

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

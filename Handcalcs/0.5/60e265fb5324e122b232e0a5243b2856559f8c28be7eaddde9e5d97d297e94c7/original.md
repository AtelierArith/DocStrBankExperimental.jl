```
set_default(; kwargs...)
```

Set default kwarg values for handcalcs. 

This works for all keyword arguments. It is additive such that if you call it multiple times, defaults will be added or replaced, but not reset.

## Kwargs

  * `cols`: sets the number of columns in the output
  * `spa`: sets the line spacing
  * `len`: can set to `:long` and it will split equation to multiple lines
  * `color`: change the color of the output (`:blue`, `:red`, etc)
  * `precision`: formats numbers to a max precision. Given `precision = 2`, `2.567` will show as `2.57`, while `2.5` would show as `2.5`
  * `h_env`: choose between "aligned" (default), "align" and other LaTeX options
  * `not_funcs`: name the functions you do not want to "unroll"
  * `parse_pipe`: a boolean value (default=true) to remove pipe from equation. This is intended for unitful equations.
  * `parse_ifs`: a boolean value (default=true) to unroll if statements. Function unrolling works and it only shows the parts of the if statement that were met.
  * `disable`: disable handcalcs rendering to run simulations and turn it back on when needed.

Example: 

```julia
set_handcalcs(cols = 2, spa = 5)
```

To reset the defaults that you have set, use `reset_handcalcs`. To see your specified defaults, use `get_handcalcs`.

```
get_handcalcs()
```

Get a Dict with the user-specified default kwargs for handcalcs, set by `set_handcalcs`.

## Kwargs

  * `cols`: sets the number of columns in the output
  * `spa`: sets the line spacing
  * `len`: can set to `:long` and it will split equation to multiple lines
  * `h_env`: Choose between "aligned" (default), "align" and other LaTeX options
  * `precision`: formats numbers to a max precision. Given `precision = 2`, `2.567` will show as `2.57`, while `2.5` would show as `2.5`
  * `not_funcs`: Name the functions you do not want to "unroll"
  * `parse_pipe`: a boolean value (default=true) to remove pipe from equation. This is intended for unitful equations.
  * `parse_ifs`: a boolean value (default=true) to unroll if statements. Function unrolling works and it only shows the parts of the if statement that were met.
  * `disable`: disable handcalcs rendering to run simulations and turn it back on when needed.

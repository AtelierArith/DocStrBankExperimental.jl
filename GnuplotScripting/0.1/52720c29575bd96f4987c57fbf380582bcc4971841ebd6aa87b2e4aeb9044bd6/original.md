```julia
free_form(gp::GnuplotScript,gp_line::AbstractString)
```

Write gnuplot commands. This command line is directly forwarded to Gnuplot. The only difference is that you can use `replot` even for the first plot. This is convenient when you chain plots, you do not have to worry if the current command is the first plot.

# Usage example

```julia
using GnuplotScripting

gp = GnuplotScript()

free_form(gp, "replot sin(x) lw 2 t 'a trigonometric function'")
```

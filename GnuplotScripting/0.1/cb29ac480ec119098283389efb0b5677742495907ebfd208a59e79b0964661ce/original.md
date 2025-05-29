```
write_script(script_file::AbstractString,gp::GnuplotScript)
```

Write script with embedded data for future use.

# Usage

```julia
gp = GnuplotScript()

...

write_script("gnuplot_script.gp",gp)
```

You can replay the script using Gnuplot:

```sh
    gnuplot gnuplot_script.gp
```

If you want to keep the gnuplot session opened, add a final `-`

```sh
    gnuplot gnuplot_script.gp -
```

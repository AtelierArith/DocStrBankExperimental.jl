```julia
gp = GnuplotScript(;direct_plot = true)
```

Create a gnuplot script `gp`. If `direct_plot` is true, simultaneously plot the registered operations.

# Usage example

You can perform a simple plot as follows:

```julia
gp = GnuplotScript(;direct_plot = true)

X=[-pi:0.1:pi;];
Ys = sin.(X);
Yc = cos.(X);

id = register_data(gp,hcat(X,Ys,Yc))
free_form(gp,"replot '$id' u 1:3 w l t 'cos'")
free_form(gp,"replot '$id' u 1:2 w l t 'sin'")
```

The plot will be created immediately.

# Also see

  * [`register_data`](@ref)
  * [`free_form`](@ref)

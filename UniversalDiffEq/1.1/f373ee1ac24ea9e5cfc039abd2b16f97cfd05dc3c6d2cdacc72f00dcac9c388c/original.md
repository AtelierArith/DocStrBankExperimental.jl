```
plot_bifurcation_diagram(model::UDE, xvariable; N = 25, color_variable= nothing, conditional_variable = nothing, size= (600, 400))
```

This function returns a plot of the equilibrium values of the state varaibles $y_t$ as a funciton of the covariates $X_t$. The arguemnt `xvariable` determines the covariate plotted on the x-axis. Additional variables can be visualized in sperate panel by specifying the `conditional_variable` key word argument or visualized by the color scheme using the `color_variable` argument.

The key word arguent `size` controls the dimensions of the final plot.

```
plot_Nyquist!(plt,a;label)
```

Adds circuits to pre-existing Nyquist plot

# Arguments

  * `plt`: The input Nyquist plot to manipulate
  * `a::Circuit`: The circuits to add to the Nyquist plot
  * `label`: kwarg label for plot

# Examples

```julia
julia> using EISAnalysis
julia> eval(initialize());
julia> circuit1 = r-r/c;
julia> circuit2 = r-r/q;
julia> plot_Nyquist(circuit1,circuit2;label= ["R-C Circuit","R-CPE Circuit"]);
```

```
wiggle(args...[; kwargs...])
wiggle(plt, args...[; kwargs...])
```

Plots a set of shaded wiggles.

# Arguments

  * `plt::Plots.Plot`: Input plot to plot shaded wiggles.
  * `args...`: Additional positional arguments for `wiggle`. See [`wiggle!`](@ref).

# Keyword Arguments

  * `kwargs...`: Keyword arguments for `wiggle`. See [`wiggle!`](@ref).

# Returns

`::Plots.Plot`: Shaded wiggles on top of current plot object.

# Examples

```julia
using Plots, WaveletsExt

# Generate random signals
x = randn(16, 5)

# ----- Build wiggles -----
# Method 1
wiggle(x)

# Method 2
p = Plot()
wiggle(p, x)
```

Translated by Nicholas Hausch – MATLAB file provided by Naoki Saito. The previous MATLAB version contributors are Anthony K. Booer (SLB) and Bradley Marchand (NSWC-PC).  

Revised by Naoki Saito, Feb. 05, 2018. Maintained by Zeng Fung Liew for newest Julia version compatibility. 

**See also:** [`wiggle!`](@ref)

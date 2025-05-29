```
spg(f, g!, fg!, x, funProj, options; ls=nothing, callback=nothing)
```

Function for using Spectral Projected Gradient to solve problems of the form min funObj(x) s.t. x in C

# Arguments

  * `f(x)`: function to minimize (returns objective only)
  * `g!(g, x)`: gradient of function (in place)
  * `fg!(g, x)`: objective and gradient (in place)
  * `funProj(x)`: function that returns projection of x onto C
  * `x`: Initial guess
  * `options`: spg_options structure

# Optional Arguments

  * `ls` `: User provided linesearch function
  * `callback` : Callback function. Must take as input a `result` callback(x::result)

# Notes:

  * if the projection is expensive to compute, you can reduce the     number of projections by setting testOpt to 0 in the options
  * Adapted fromt he matlab implementation of minConf_SPG

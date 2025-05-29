```
orbit(sol::AbstractODESolution; vars=nothing, tspan=nothing, to_3d::Bool=false, interactive::Bool=true)
```

A plot recipe for plotting orbit or other figures related to six phase space coordinates and time.

# Arguments

  * `sol::AbstractODESolution`: the solution returned by the ODE solver.

# Keywords

  * `vars`: the argument used to choose variables to be plotted. Default value is [(1, 2, 3)].
  * `tspan::Tuple`: the span of time to be plotted. For example, tspan = (0, 1).
  * `to_3d::Bool`: whether to force the points to be plotted in 3d. If `true`, the order of

coordinates will be rearranged for plotting as 3d points.

  * `interactive::Bool`: whether to show the figure in interactive mode.

## vars

`vars` can be an Integer, Function, Tuple and Array. The basic form for `vars` is Tuple. For example, if you want to plot the variable `x` as a function of time or the orbit of a particle, you can use it like this:

```julia
orbit(sol, vars=(0, 1))
orbit(sol, vars=(1, 2, 3))
```

If the length of the tuple is 3, it will be converted to 3d. To plot a function of time, position or velocity, you can first define the function. The arguments of the function must be a 7-dimensional array, the elements of which correspond to the phase space coordinates and time, and the return value must be a Number. For example,

```julia
Eₖ(xu) = mₑ*(xu[4]^2 + xu[5]^2 + xu[6]^2)/2
orbit(sol, vars=(0, Eₖ))
```

This command will plot the kinetic energy as a function of x. The above form is equivalent to

```julia
orbit(sol, vars=Eₖ)
orbit(sol, vars=1)
```

Plotting multiple lines at one time are supported by providing a tuple of indexes. For example,

```julia
orbit(sol, vars=[1, (1, 2), Eₖ])
```

There are some more advanced usages. If a tuple contains vectors, they will be expanded automatically. For example,

```julia
orbit(sol, vars=(0, [1, 2, 3]))
orbit(sol, vars=([1, 2, 3], [4, 5, 6]))
```

are equivalent to

```julia
orbit(sol, vars=[(0, 1), (0, 2), (0, 3)])
orbit(sol, vars=[(1, 4), (2, 5), (3, 6)])
```

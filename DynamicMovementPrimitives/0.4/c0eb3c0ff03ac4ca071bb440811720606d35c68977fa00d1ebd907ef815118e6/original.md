`t,y,z,x = solve(dmp, t = 0:length(dmp.t)-1; y0 = _1(dmp), g = dmp.g, solver=ode45)`

`t` time vector

## Keyword arguments:

`y0` start position, defaults to the initial point in training data from `dmp` `g` goal, defaults to goal from `dmp`

`solver` the ode solver to use, see https://github.com/JuliaLang/ODE.jl 

The default solver is `solver=ode54`, a faster alternative is `solver=euler`

see also `plotdmp`

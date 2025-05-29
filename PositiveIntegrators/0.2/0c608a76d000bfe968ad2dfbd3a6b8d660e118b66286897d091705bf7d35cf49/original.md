```
isnegative(sol::ODESolution)
```

Returns `true` if `sol.u` contains negative elements.

Please note that negative values may occur when plotting the solution, depending on the interpolation used.

See also [`isnonnegative`](@ref).

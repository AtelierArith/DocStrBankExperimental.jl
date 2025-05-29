```
y, t, x = step(sys[, tfinal])
y, t, x = step(sys[, t])
```

Calculate the response of the system `sys` to a unit step at time `t = 0`.  If the final time `tfinal` or time vector `t` is not provided,  one is calculated based on the system pole locations. 

The return value is a structure of type `SimResult`.  A `SimResul` can be plotted by `plot(result)`,  or destructured as `y, t, x = result`. 

`y` has size `(ny, length(t), nu)`, `x` has size `(nx, length(t), nu)`

See also [`stepinfo`](@ref) and [`lsim`](@ref).

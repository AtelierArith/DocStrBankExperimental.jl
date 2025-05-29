```
y, t, x = impulse(sys[, tfinal])
y, t, x = impulse(sys[, t])
```

Calculate the response of the system `sys` to an impulse at time `t = 0`.  For continous-time systems, the impulse is a unit Dirac impulse.  For discrete-time systems, the impulse lasts one sample and has magnitude `1/Ts`.  If the final time `tfinal` or time vector `t` is not provided,  one is calculated based on the system pole locations. 

The return value is a structure of type `SimResult`.  A `SimResul` can be plotted by `plot(result)`,  or destructured as `y, t, x = result`.

`y` has size `(ny, length(t), nu)`, `x` has size `(nx, length(t), nu)`

See also [`lsim`](@ref).

```julia
function rhs!(du, u, p, t)
    # Example of a simple ODE: du/dt = -u
    du[1] = -u[1]
end
```

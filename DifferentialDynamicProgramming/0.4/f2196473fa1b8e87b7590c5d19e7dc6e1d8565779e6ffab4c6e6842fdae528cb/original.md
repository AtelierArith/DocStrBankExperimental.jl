```
demo_pendcart(;kwargs...)
```

Run the iLQG Function to find an optimal trajectory For the "pendulum on a cart system". Requires package ControlSystems.jl

# Arguments

`x0     = [π-0.6,0,0,0]` `goal   = [π,0,0,0]` `Q      = Diagonal([10,1,2,1])` : State weight matrix `R      = 1`                    : Control weight matrix `lims   = 5.0*[-1 1]`           : control limits, `T      = 600`                  : Number of time steps `doplot = true`                 : Plot results

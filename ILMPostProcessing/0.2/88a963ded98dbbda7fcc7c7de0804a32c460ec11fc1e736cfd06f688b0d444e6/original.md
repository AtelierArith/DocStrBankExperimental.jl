```
displacement_field(u::Function,v::Function,x0,y0,Trange::Tuple[;dt=:auto,alg=Euler()])
```

Calculate the displacement of particles initally at coordinates `x0` and `y0` over the range of times `Trange = (ti,tf)`, using the  velocity functions `u` and `v`.  These function can either be autonomous (taking only x and y arguments) or non-autonomous, taking an additional time argument. The final time in `Trange` can be earlier than the initial time if backward trajectories are desired. The optional keyword arguments are `dt`, the time step size (which defaults to `:auto`, for adaptive time marching, but could be specified to override this). The default time marching algorithm is `Tsit5()`. 

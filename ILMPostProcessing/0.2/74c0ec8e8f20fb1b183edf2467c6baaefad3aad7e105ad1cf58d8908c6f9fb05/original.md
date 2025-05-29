```
displacement_field(v::VectorFieldSequence,x0,y0,Trange::Tuple[;dt=step(tr),alg=Euler()])
```

Calculate the displacement of particles initally at coordinates `x0` and `y0` over the range of times `Trange = (ti,tf)`, using the sequence of spatially-interpolated velocity fields in `v`. (One can also provide the vector of velocity fields and the time array as separate arguments). The final time in `Trange` can be earlier than the initial time if backward trajectories are desired. The optional keyword arguments are `dt`, the time step size (which defaults to the step size in `tr`, but could be an integer multiple larger than 1). 

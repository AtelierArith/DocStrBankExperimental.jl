compute_trajectory(v::VectorFieldSequence,X₀,Trange::Tuple[;dt=step(tr),alg=Euler()])

Calculate the trajectories of particles with initial location(s) `X₀`. The argument `v` contains a sequence of spatially-interpolated velocity fields and an associated time array. (One can also provide the vector of velocity fields and the time array as separate arguments).

`X₀` can be specified as either a single vector `[x0,y0]`, a vector of vectors specifying x, y pairs, or a tuple of vectors or arrays specifying x and y positions, respectively, for multiple tracer particles. `Trange` is a tuple of the starting and ending integration times. The optional keyword arguments are `dt`, the time step size (which defaults to the step size in `tr`, but could be an integer multiple larger than 1). The output is the solution structure for the `OrdinaryDiffEq` package.

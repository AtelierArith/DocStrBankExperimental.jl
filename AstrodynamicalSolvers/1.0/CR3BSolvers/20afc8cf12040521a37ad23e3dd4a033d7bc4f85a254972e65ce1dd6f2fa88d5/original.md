```julia
halo(μ, lagrange; amplitude, phase, hemisphere, kwargs...)

```

!!! warning "CR3BP Dynamics"
    This computation is valid for Circular Restricted Three Body Problem dynamics.


Given a nondimensional mass parameter `μ`, and orbit characteristics, construct  an initial guess using Richardson's analytical solution, and iterate on that guess using a differential corrector. 

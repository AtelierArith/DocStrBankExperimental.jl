```
SemidiscretizationEulerAcoustics(semi_acoustics::SemiAcoustics, semi_euler::SemiEuler;
                                 source_region=x->true, weights=x->1.0)
```

!!! warning "Experimental code"
    This semidiscretization is experimental and may change in any future release.


Construct a semidiscretization of the acoustic perturbation equations that is coupled with the compressible Euler equations via source terms for the perturbed velocity. Both semidiscretizations have to use the same mesh and solvers with a shared basis. The coupling region is described by a function `source_region` that maps the coordinates of a single node to `true` or `false` depending on whether the point lies within the coupling region or not. A weighting function `weights` that maps coordinates to weights is applied to the acoustic source terms. Note that this semidiscretization should be used in conjunction with [`EulerAcousticsCouplingCallback`](@ref) and only works in two dimensions.

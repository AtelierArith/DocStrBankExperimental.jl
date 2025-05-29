```
ComputeGeodesic(DM::DataModel, InitialPos::AbstractVector, InitialVel::AbstractVector, Endtime::Number=50.;
                                Boundaries::Union{Function,Nothing}=nothing, tol::Real=1e-11, approx::Bool=false, meth=Tsit5())
```

Constructs geodesic with given initial position and velocity. It is possible to specify a boolean-valued function `Boundaries(u,t,int)`, which terminates the integration process when it returns `true`.

By setting the keyword `approx=true`, the ChristoffelSymbols are assumed to be constant and only computed once at the initial position. This simplifies the computation immensely but may also constitute an inaccurate approximation depending on the magnitude of the Ricci curvature.

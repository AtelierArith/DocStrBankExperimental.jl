```
judiRHS
    dt::Vector{T}
    geometry::Geometry
    data
```

Abstract sparse vector for right-hand-sides of the modeling operators. The `judiRHS` vector has the
dimensions of the full time history of the wavefields, but contains only the data defined at the 
source or receiver positions (i.e. wavelets or shot records).

# Constructor

```
judiRHS(dt, geometry, data)
```

# Examples

Assuming `Pr` and `Ps` are projection operators of type `judiProjection` and `dobs` and `q` are
seismic vectors of type `judiVector`, then a `judiRHS` vector can be created as follows:     rhs = Pr'*dobs    # right-hand-side with injected observed data     rhs = Ps'*q    # right-hand-side with injected wavelet

```
sourceintegration(x::Vector,env::Environment,limits::Vector{T}) where T
sourceintegration(x::Vector,env::Environment,limits::Vector{Vector{T}}) where T
sourceintegration(x::FreqArray,env::Environment,limits::Vector{T}) where T
sourceintegration(x::FreqArray,env::Environment,limits::Vector{Vector{T}}) where T
```

Source integration of `x` from `limits` given in cartesian coordinates `[xmin,xmax,ymin,ymax]`.

```
src1 = [-0.1,0.1,-0.1,0.1]
src2 = [-0.2,0.0,-0.1,0.1]
limits = [src1,src2]
srcint = sourceintegration(x,env,limits)
```

Optionally supply keyword `int_thres` to set a threshold on source integration. Default is set to `Inf` which sum all values within integration region.

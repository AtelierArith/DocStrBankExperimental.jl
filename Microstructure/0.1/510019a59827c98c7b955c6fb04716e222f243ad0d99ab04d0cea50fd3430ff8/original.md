```
Protocol(
bval::Vector{Float64}
techo::Vector{Float64}
tdelta::Vector{Float64}
tsmalldel::Vector{Float64}
gvec::Vector{Float64}
bvec::Matrix{Float64}
nmeas::Vector{Float64}
)
```

Return a Protocol Type object to hold parameters in acquisition protocol relavent for modelling  including b-values, tcho times, diffusion gradient seperation, duration, strengh, direction and the number of measurements.  Unit convention: most text files use s/mm^2 for b-values and ms for time while they are converted to SI unit in the Protocol. b-values (s/m^2); time (s); size (m); G (T/m) 

```
Protocol(
    filename::String
)
```

Return a Protocol Type object from a b-table file generated from spherical_mean function.

```
Protocol(
    bval::Vector{Float64},
    techo::Vector{Float64},
    tdelta::Vector{Float64},
    tsmalldel::Vector{Float64},
)
```

Calculate `gvec` and return a Ptotocol Type object from provided parameters; other fields are not useful

```
Protocol(
    dmri::dMRI
)
```

Return a Protocol Type object from a dMRI object.

```
update_j4osc_mean_elements_epoch!(j4oscd::J4OsculatingPropagator, orb::KeplerianElements, new_epoch::Union{Number, DateTime}) -> KepleriranElements
```

Update the epoch of the mean elements `orb` using the propagator `j4oscd` to `new_epoch`, which can be represented by a Julian Day or a `DateTime`.

!!! note
    The J4 osculating orbit propagator `j4oscd` will be initialized with the Keplerian elements returned by the function.


# Examples

```julia-repl
julia> orb = KeplerianElements(
           DateTime("2023-01-01") |> datetime2julian,
           7190.982e3,
           0.001111,
           98.405 |> deg2rad,
           90     |> deg2rad,
           200    |> deg2rad,
           45     |> deg2rad
       )
KeplerianElements{Float64, Float64}:
           Epoch :    2.45995e6 (2023-01-01T00:00:00)
 Semi-major axis : 7190.98     km
    Eccentricity :    0.001111
     Inclination :   98.405    °
            RAAN :   90.0      °
 Arg. of Perigee :  200.0      °
    True Anomaly :   45.0      °

# Allocate a new J4 osculating orbit propagator using the created Keplerian elements. Notice
# that any set of Keplerian elements can be used here.
julia> j4oscd = j4osc_init(orb);

julia> update_j4osc_mean_elements_epoch!(j4oscd, orb, DateTime("2023-01-02"))
KeplerianElements{Float64, Float64}:
           Epoch :    2.45995e6 (2023-01-02T00:00:00)
 Semi-major axis : 7190.98     km
    Eccentricity :    0.001111
     Inclination :   98.405    °
            RAAN :   90.9555   °
 Arg. of Perigee :  197.079    °
    True Anomaly :  127.293    °
```

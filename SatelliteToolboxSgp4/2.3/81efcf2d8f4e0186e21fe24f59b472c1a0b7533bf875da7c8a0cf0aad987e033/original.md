```
update_sgp4_tle_epoch!(sgp4d::Sgp4Propagator, tle::TLE, new_epoch::Union{Number, DateTime}; kwargs...) -> TLE
```

Update the `tle` epoch with SGP4 mean elements to `new_epoch` using the orbit propagator `sgp4d`. `new_epoch` can be represented by a Julian Day or a `DateTime`.

!!! notes
    The SGP4 orbit propagator `sgp4d` will be initialized with the TLE returned by the function.


This function uses the following algorithm to update the TLE epoch:

1. Initialize the SGP4 propagator with `tle`;
2. Propagate the orbit to `new_epoch` and obtain the osculating state vector in TEME  reference frame; and
3. Fit a new TLE that provides the same osculating state vector but considering the new  epoch.

The third step uses the function [`fit_sgp4_tle!`](@ref). Hence, some keywords are related to it. For more information, see the documentation of [`fit_sgp4_tle!`](@ref).

# Keywords

  * `atol::Number`: Tolerance for the residue absolute value. If, at any iteration, the   residue is lower than `atol`, the computation loop stops.   (**Default** = 2e-4)
  * `rtol::Number`: Tolerance for the relative difference between the residues. If, at any   iteration, the relative difference between the residues in two consecutive iterations is   lower than `rtol`, the computation loop stops.   (**Default** = 2e-4)
  * `max_iterations::Int`: Maximum number of iterations allowed for the least-square fitting.   (**Default** = 50)
  * `verbose::Bool`: If `true`, the algorithm prints debugging information to `stdout`.   (**Default** = true)

# Examples

```julia-repl
julia> tle = tle"""
          AMAZONIA 1
          1 47699U 21015A   23083.68657856  .00000000  00000-8  43000-3 0  9999
          2 47699  98.4304 162.1097 0001247 136.2017 223.9283 14.40814394108652
          """
TLE:
                      Name : AMAZONIA 1
          Satellite number : 47699
  International designator : 21015A
        Epoch (Year / Day) : 23 /  83.68657856 (2023-03-24T16:28:40.388)
        Element set number : 999
              Eccentricity :   0.00012470
               Inclination :  98.43040000 deg
                      RAAN : 162.10970000 deg
       Argument of perigee : 136.20170000 deg
              Mean anomaly : 223.92830000 deg
           Mean motion (n) :  14.40814394 revs / day
         Revolution number : 10865
                        B* :      0.00043 1 / er
                     ṅ / 2 :            0 rev / day²
                     n̈ / 6 :            0 rev / day³

# Allocate a new SGP4 orbit propagator using the created TLE. Notice that any TLE can be
# used here.
julia> sgp4d = sgp4_init(tle)

julia> update_sgp4_tle_epoch!(sgp4d, tle, DateTime("2023-06-19"))
ACTION:   Fitting the TLE.
           Iteration        Position RMSE        Velocity RMSE           Total RMSE       RMSE Variation
                                     [km]             [km / s]                  [ ]
PROGRESS:          4          2.79523e-06          2.57681e-09          2.79523e-06             -99.9999 %

TLE:
                      Name : AMAZONIA 1
          Satellite number : 47699
  International designator : 21015A
        Epoch (Year / Day) : 23 / 170.00000000 (2023-06-19T00:00:00)
        Element set number : 999
              Eccentricity :   0.00012727
               Inclination :  98.43040000 deg
                      RAAN : 247.20081879 deg
       Argument of perigee : 237.78423781 deg
              Mean anomaly : 121.83893462 deg
           Mean motion (n) :  14.41052177 revs / day
         Revolution number : 10865
                        B* :      0.00043 1 / er
                     ṅ / 2 :            0 rev / day²
                     n̈ / 6 :            0 rev / day³
```

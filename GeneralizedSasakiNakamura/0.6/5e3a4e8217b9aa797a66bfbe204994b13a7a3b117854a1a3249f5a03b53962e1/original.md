```
Teukolsky_radial(s::Int, l::Int, m::Int, a, omega; data_type=Solutions._DEFAULTDATATYPE, ODE_algorithm=Solutions._DEFAULTSOLVER, tolerance=Solutions._DEFAULTTOLERANCE, method="auto")
```

Compute the Teukolsky function for a given mode (specified by `s` the spin weight, `l` the harmonic index, `m` the azimuthal index, `a` the Kerr spin parameter, and `omega` the frequency) with the purely-ingoing boundary condition at the horizon (`IN`) and the purely-outgoing boundary condition at infinity (`UP`).

Note that for *real* frequencies, the numerical inner boundary (rsin) and outer boundary (rsout) are set to the default values `_DEFAULT_rsin` and `_DEFAULT_rsout`, respectively, while the order of the asymptotic expansion at the horizon and infinity are determined automatically. As for *complex* frequencies, the numerical inner and the outer boundaries are determined automatically, while the order of the asymptotic expansion at the horizon and infinity are set to `_DEFAULT_horizon_expansion_order_for_cplx_freq` and `_DEFAULT_infinity_expansion_order_for_cplx_freq`, respectively.

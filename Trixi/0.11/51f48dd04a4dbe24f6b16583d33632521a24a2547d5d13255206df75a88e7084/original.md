```
min_max_speed_einfeldt(u_ll, u_rr, orientation::Integer, equations)
min_max_speed_einfeldt(u_ll, u_rr, normal_direction::AbstractVector, equations)
```

More advanced mininmal and maximal wave speed computation based on

  * Bernd Einfeldt (1988) On Godunov-type methods for gas dynamics. [DOI: 10.1137/0725021](https://doi.org/10.1137/0725021)
  * Bernd Einfeldt, Claus-Dieter Munz, Philip L. Roe and Björn Sjögreen (1991) On Godunov-type methods near low densities. [DOI: 10.1016/0021-9991(91)90211-3](https://doi.org/10.1016/0021-9991(91)90211-3)

originally developed for the compressible Euler equations. A compact representation can be found in [this lecture notes, eq. (9.28)](https://metaphor.ethz.ch/x/2019/hs/401-4671-00L/literature/mishra_hyperbolic_pdes.pdf).

See also [`FluxHLL`](@ref), [`min_max_speed_naive`](@ref), [`min_max_speed_davis`](@ref).

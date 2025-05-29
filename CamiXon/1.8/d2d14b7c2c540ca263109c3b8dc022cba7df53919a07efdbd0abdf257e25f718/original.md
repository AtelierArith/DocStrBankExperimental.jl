```
dictAntoineCoefficient
```

Antoine coefficients [A,B,C,D] for temperature ranges below and above the melting points from [`dictMeltingPoint`](@ref). These coefficients are used  in the Antoine equation to calculate the saturated vapor pressure *p* (in Pa)  at temperature `*T* (in K),

$$
\mathrm{log_{e}}p=A+B/T+C\mathrm{log_{10}}T+D\cdot T/1000.
$$

Currently, only the coefficients for the metalic elements are implemented - see C. B. Alcock, V. P. Itkin and M. K. Horrigan, Canadian Metallurgical Quarterly, 23, 309 (1984).

Note that the melting point is taken to be pressure independent.

```
julia> dictAntoineCoefficient
Dict{Int64, Tuple{Any, Any, Tuple{Any, Any, Any}}} with 102 entries:
  5  => (nothing, nothing, (empty, 2349.0, empty))
  56 => ([40.0897, -22312.0, -5.27062, 0.0], [20.7526, -18796.0, 0.0, 0.0], (298.0, 1000.0, 1200.0))
  35 => (nothing, nothing, (empty, 265.8, empty))
  55 => ([22.3736, -9208.04, 0.0, 0.0], [21.1164, -8818.9, 0.0, 0.0], (298.0, 301.7, 550.0))
  60 => ([32.2402, -39751.8, -2.19183, 0.0], [22.8364, -36436.1, 0.0, 0.0], (298.0, 1297.0, 2000.0))
  30 => ([25.5765, -15602.3, 0.0, 0.0], [23.9094, -14474.0, 0.0, 0.0], (298.0, 692.68, 750.0))
  32 => (nothing, nothing, (empty, 1211.4, empty))
  ⋮  => ⋮
```

#### Examples:

To calculate the saturated vapor pressure of Li (in Pa) at T=623 K we use the Antoine equation implemented in thefunction [`svp`](@ref).

```
julia> svp(55, 400)
0.39420306801845933

julia> svp("Cs", 400)
0.39420306801845933
```

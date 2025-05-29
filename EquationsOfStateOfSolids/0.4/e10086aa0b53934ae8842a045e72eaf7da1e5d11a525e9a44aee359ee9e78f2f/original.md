```
PoirierTarantola3rd(v0, b0, b′0, e0=zero(v0 * b0))
```

Create a Poirier–Tarantola third order equation of state.

This equation of state can have units. The units are specified in [`Unitful.jl`](https://github.com/PainterQubits/Unitful.jl)'s `@u_str` style.

# Arguments

  * `v0`: the volume of solid at zero pressure.
  * `b0`: the bulk modulus of solid at zero pressure.
  * `b′0`: the first-order pressure-derivative bulk modulus of solid at zero pressure.
  * `e0`: the energy of solid at zero pressure.

```
@unitdim(D,U,S,L)
```

Specify print `S::String` and LaTeX `L::String` for derived dimension `D` in `U::UnitSystem`.

```Julia
@unitdim magneticflux Gauss "Mx" "\text{Mx}"
@unitdim magneticfluxdensity Gauss "G" "\text{G}"
@unitdim magneticfield Gauss "Oe" "\text{Oe}"
@unitdim frequency Metric "Hz" "\text{Hz}"
@unitdim force Metric "N" "\text{N}"
@unitdim pressure Metric "Pa" "\text{Pa}"
@unitdim energy Metric "J" "\text{J}"
@unitdim power Metric "W" "\text{W}"
@unitdim mass British "slug" "\text{slug}"
@unitdim force FPS "pdl" "\text{pdl}"
```

These standard examples are some of the built-in defaults.

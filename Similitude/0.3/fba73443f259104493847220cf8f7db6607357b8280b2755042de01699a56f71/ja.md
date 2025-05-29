```
@unitdim(D,U,S,L)
```

派生次元 `D` のために、`U::UnitSystem` で `S::String` と LaTeX `L::String` を指定します。

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

これらの標準的な例は、組み込みのデフォルトの一部です。

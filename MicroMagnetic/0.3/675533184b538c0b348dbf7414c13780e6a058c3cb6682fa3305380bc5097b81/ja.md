```
add_dmi(sim::MicroSim, D::NumberOrTupleOrArrayOrFunction; name="dmi", type="bulk")
```

システムにDMIを追加します。 `type`は"bulk"、"interfacial"、または"D2d"のいずれかです。

例:

```julia
   add_dmi(sim, 1e-3, type="interfacial")
```

または

```julia
   add_dmi(sim, 1e-3, type="D2d")
```

```julia
   add_dmi(sim, (1e-3, 1e-3, 0), type="bulk")
```

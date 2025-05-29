```
add_dmi(sim::MicroSim, D::NumberOrTupleOrArrayOrFunction; name="dmi", type="bulk")
```

Add DMI to the system. `type` could be "bulk", "interfacial" or "D2d". 

Examples:

```julia
   add_dmi(sim, 1e-3, type="interfacial")
```

or

```julia
   add_dmi(sim, 1e-3, type="D2d")
```

```julia
   add_dmi(sim, (1e-3, 1e-3, 0), type="bulk")
```

```
System(abstract_system; force_units=u"kJ * mol^-1 * nm^-1", energy_units=u"kJ * mol^-1")
```

Convert an AtomsBase `AbstractSystem` to a Molly `System`.

`force_units` and `energy_units` should be set as appropriate. To add properties not present in the AtomsBase interface (e.g. pair potentials) use the convenience constructor `System(sys::System)`.

```
EquilibriumRegion(model, p_datum = missing,
    datum_depth = missing;
    woc = NaN,
    goc = NaN,
    wgc = NaN,
    pc_woc = 0.0,
    pc_goc = 0.0,
    pc_wgc = 0.0,
    temperature = missing,
    temperature_vs_depth = missing,
    composition = missing,
    composition_vs_depth = missing,
    liquid_composition = missing,
    liquid_composition_vs_depth = missing,
    vapor_composition = missing,
    vapor_composition_vs_depth = missing,
    density_function = missing,
    rs = 0.0,
    rs_vs_depth = missing,
    rv = 0.0,
    rv_vs_depth = missing,
    pvtnum = 1,
    satnum = 1,
    cells = missing,
    kwarg...
)
```

Set uip equilibriation region for a reservoir model. The region is defined by the datum pressure and depth, and the water-oil, gas-oil, and water-gas contacts. The contacts will be used to determine the phase distribution and initial pressure in the region. The region can be further specified by temperature, composition, density, and rs/rv functions. Most entries can either be specified as a function of depth or as a constant value. Additional keyword arguments are passed onto the `equilibriate_state` function.

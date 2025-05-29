```
BlackOilUnknown(dr_max = Inf, ds_max = Inf)
```

Variable defining the variable switching black-oil variable. The `ds_max` argument limits the maximum saturation change over a single Newton iteration when both a oileic and gaseous phase is present. The `dr_max` limits the maximum change in the undersaturated variable, taken relative to the maximum value of the undersaturated variable.

During simulation, this variable can take on the following interpretations: Gas saturation, Rs or Rv, depending on the phase conditions and miscibility model.

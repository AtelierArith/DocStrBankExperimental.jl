```
use_superancillaries!(val::Bool = true)
```

Enable the use of cubic and PC-SAFT superancillaries as initial points for `saturation_pressure`. for `PCSAFT` it also enables the use of superancillaries for critical point calculations. This function requires `EoSSuperancillaries.jl` to be loaded in the current session (`using EoSSuperancillaries`).

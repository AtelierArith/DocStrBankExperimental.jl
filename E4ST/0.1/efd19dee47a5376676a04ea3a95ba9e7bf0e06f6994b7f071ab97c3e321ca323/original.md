```
add_pl_gs_bus!(config, data, model)
```

Add the `pl_gs_bus` expression to the model which is load power that qualifies for generation standards.  This includes:

  * Nominal load net any curtailed load `plnom_bus - plcurt_bus`
  * Battery loss (i.e. difference between charge and discharge)
  * Line losses

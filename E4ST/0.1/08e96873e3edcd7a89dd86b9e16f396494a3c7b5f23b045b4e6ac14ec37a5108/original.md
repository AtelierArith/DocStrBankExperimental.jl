```
modify_model!(pol::GenerationStandard, config, data, model)
```

Creates the expression :p*gs*bus, the load that generation standards are applied to, if it hasn't been created already.  Creates a constraint that takes the general form: `sum(gs_egen * credit) <= gs_value * sum(gs_load)`

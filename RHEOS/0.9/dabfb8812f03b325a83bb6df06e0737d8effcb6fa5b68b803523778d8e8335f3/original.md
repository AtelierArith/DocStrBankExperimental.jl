```
modelpredict(data::RheoTimeData, model::RheoModel; diff_method="BD")
```

Given an incomplete data set (only either stress or strain missing) and model with values substituted into parameters (`RheoModel`), return a new dataset based on the model. If data is type of `stress_only`, then the creep modulus is used; if data type is `strain_only`, the relaxation modulus is used. A complete `RheoTimeData` of type `strain_and_stress` is returned. `diff_method` sets finite difference for calculating the derivative used in the hereditary integral and can be either backwards difference (`"BD"`) or central difference (`"CD"`).

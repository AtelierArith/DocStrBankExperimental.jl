```
hrep(model::JuMP.Model)
```

Builds an H-representation from the feasibility set of the JuMP model `model`. Note that if non-linear constraint are present in the model, they are ignored.

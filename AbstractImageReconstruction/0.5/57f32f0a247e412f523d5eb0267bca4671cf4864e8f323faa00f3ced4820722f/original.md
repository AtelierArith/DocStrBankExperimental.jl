```
loadPlan(filename::Union{AbstractString, IO}, modules::Vector{Module})
```

Load a `RecoPlan` from a TOML file. The `modules` argument is a vector of modules that contain the types used in the plan. After loading the plan, the listeners are attached to the properties using `loadListener!`.

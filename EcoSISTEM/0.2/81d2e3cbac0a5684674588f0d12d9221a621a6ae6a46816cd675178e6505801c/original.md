```
simplehabitatAE(val::Union{Float64, Unitful.Quantity{Float64}},
    dimension::Tuple{Int64, Int64}, maxbud::Float64, area::Unitful.Area{Float64},
    active::Matrix{Bool})
```

Function to create a simple `ContinuousHab`, `SimpleBudget` type abiotic environment. It creates a `ContinuousHab` filled with a given value, `val`, dimensions (`dimension`) and a specified area (`area`). It also creates a `SimpleBudget` type filled with the maximum budget value (`maxbud`). The rate of temperature change is specified using the parameter `rate`. If a Bool matrix of active grid squares is included, `active`, this is used, else one is created with all grid cells active.

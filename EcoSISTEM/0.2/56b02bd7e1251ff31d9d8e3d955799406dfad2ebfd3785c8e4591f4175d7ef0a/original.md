```
simplenicheAE(numniches::Int64, dimension::Tuple,
                    maxBud::Float64, area::Unitful.Area{Float64},
                    active::Matrix{Bool})
```

Function to create a simple `DiscreteHab`, `SimpleBudget` type abiotic environment. Given a number of niche types `numniches`, it creates a `DiscreteHab` environment with dimensions `dimension` and a specified area `area`. It also creates a `SimpleBudget` type filled with the maximum budget value `maxbud`. If a Bool matrix of active grid squares is included, `active`, this is used, else one is created with all grid cells active.

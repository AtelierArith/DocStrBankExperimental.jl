```
tempgradAE(min::Unitful.Temperature{Float64},
  max::Unitful.Temperature{Float64},
  dimension::Tuple{Int64, Int64}, maxbud::Float64,
  area::Unitful.Area{Float64}, rate::Quantity{Float64, typeof(𝚯*𝐓^-1)},
  active::Matrix{Bool})
```

Function to create a temperature gradient `ContinuousHab`, `SimpleBudget` type abiotic environment. Given a `min` and `max` temperature, it generates a gradient from minimum at the bottom to maximum at the top. It creates a `ContinuousHab` environment with dimensions `dimension` and a specified area `area`. It also creates a `SimpleBudget` type filled with the maximum budget value `maxbud`. The rate of temperature change is specified using the parameter `rate`. If a Bool matrix of active grid squares is included, `active`, this is used, else one is created with all grid cells active.

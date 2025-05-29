```
peakedgradAE(minT::Unitful.Temperature{Float64},
   maxT::Unitful.Temperature{Float64},
   dimension::Tuple{Int64, Int64}, maxbud::Unitful.Quantity{Float64},
   area::Unitful.Area{Float64}, rate::Quantity{Float64, 𝚯*𝐓^-1},
   active::Matrix{Bool})
```

Function to create a temperature gradient `ContinuousHab`, `SimpleBudget` type abiotic environment. Given a `min` and `max` temperature, it generates a gradient from minima at the top and bottom peaking to maximum in the middle. It creates a `ContinuousHab` environment with dimensions `dimension` and a specified area `area`. It also creates a `SimpleBudget` type filled with the maximum budget value `maxbud`. The rate of temperature change is specified using the parameter `rate`. If a Bool matrix of active grid squares is included, `active`, this is used, else one is created with all grid cells active.

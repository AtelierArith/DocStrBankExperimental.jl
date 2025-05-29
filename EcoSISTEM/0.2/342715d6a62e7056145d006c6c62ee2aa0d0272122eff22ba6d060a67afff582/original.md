```
raingrad(minT::Unitful.Temperature{Float64}, maxT::Unitful.Temperature{Float64},
  size::Unitful.Length{Float64},
  dim::Tuple{Int64, Int64}, rate::Quantity{Float64, 𝚯*𝐓^-1})
```

Function to create a `ContinuousHab` habitat with a rainfall gradient.

```
eikr = Eikr(eikar, eikbr, eikcr)
```

mutable struct for holding the eikr vectors

# Attributes

  * `eikar::OffsetArray{Complex{Float64}}`: array for storing e^{i * ka ⋅ r}; has indices 0:kreps[1] and corresponds to recip. vectors in a-direction
  * `eikbr::OffsetArray{Complex{Float64}}`: array for storing e^{i * kb ⋅ r}; has indices -kreps[2]:kreps[2] and corresponds to recip. vectors in b-direction
  * `eikcr::OffsetArray{Complex{Float64}}`: array for storing e^{i * kc ⋅ r}; has indices -kreps[2]:kreps[1] and corresponds to recip. vectors in c-direction

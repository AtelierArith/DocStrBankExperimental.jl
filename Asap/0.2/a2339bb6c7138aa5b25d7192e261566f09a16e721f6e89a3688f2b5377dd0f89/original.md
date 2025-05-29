```
GravityLoad(element::Element, factor::Float64)
```

A gravity load (negative global Z) applied along a member. 

Generates distributed load w = element.section.A * element.section.ρ * factor, where factor should be the appropriate acceleration due to gravity.

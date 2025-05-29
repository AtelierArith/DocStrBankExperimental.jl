```
rt_ports(Γ::Mesh, γ::Mesh ...)
```

Constructs the RT space on `Γ`, relative to boundary pairs in `γ`. `γ` expects any number of pairs-of-ports as arguments and accepts tuples, arrays, vectors etc. e.g `rt_ports(Γ, a, b ...);` where a = [γ₁ γ₂], b = (γ₃,γ₄) etc. `rt_ports` with no pair of ports supplied i.e `rt_ports(Γ)` reduces to the `raviartthomas(Γ)` function. The RT space ensures current continuity in each pair of ports. i.e. current leaving mesh Γ through γ₁ is accounted for in γ₂.

Returns the RT basis object.

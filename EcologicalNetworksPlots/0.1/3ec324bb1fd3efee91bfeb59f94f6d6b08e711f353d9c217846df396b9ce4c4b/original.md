```
ForceDirectedLayout
```

The fields are, in order:

  * `move`, a tuple to specify whether moves on the x and y axes are allowed
  * `k`, a tuple (kₐ,kᵣ) giving the strength of attraction and repulsion
  * `exponents`, a tuple (a,b,c,d) giving the exponents for the attraction and repulsion functions
  * `gravity`, the strength of attraction towards the center, set to `0.0` as a default
  * `δ`, a floating point constant regulating the attractive force of interaction strength – when set to its default value of 0.0, all edges have the same attraction
  * `degree`, a boolean to specificy whether the nodes repel one another according to their degree

The various coefficients are used to decide how strongly nodes will *attract* or *repel* one another, as a function of their distance Δ. Specifically, the default is that connected nodes will attract one another proportionally to (Δᵃ)×(kₐᵇ), with a=2 and b=-1, and all nodes repel one another proportionally to (Δᶜ)×(kᵣᵈ) with c=-1 and d=2.

The parameterization for the Fruchterman-Rheingold layout is the default one, particularly if kₐ=kᵣ. The Force Atlas 2 parameters are kₐ=1 (or b=0), kᵣ set to any value, a=1, c=-1, d=1. Note that in all cases, the gravity is a multiplying constant of the resulting attraction force, so it will also be sensitive to these choices. The `FruchtermanRheingold` and `ForceAtlas2` functions will return a `ForceDirectedLayout` – as this object is mutable, you can replace the exponents at any time.

The δ parameter is particularly important for probabilistic networks, as these tend to have *all* their interactions set to non-zero values. As such, setting a value of δ=1 means that the interactions only attract as much as they are probable.

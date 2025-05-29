```
PlanarBody(curve::NurbsCurve;map)       # creates NurbsLocator
PlanarBody(curve,lims::Tuple;T,map,mem) # creates HashedLocator
```

Embeds a ParametricBody onto the `ζ₃=0` plane defined by `map`. The `curve`  defines the planform of a planar body with minimial thickness `thk=ϵ+√3/2`.  See Lauber & Weymouth 2022. Note, the velocity is defined soley from `dot(map)`.

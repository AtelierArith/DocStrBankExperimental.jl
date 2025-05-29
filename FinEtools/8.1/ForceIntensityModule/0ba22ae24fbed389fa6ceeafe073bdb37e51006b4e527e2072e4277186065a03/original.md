```
ForceIntensity{T<:Number, F<:Function}
```

Distributed force (force intensity) type.

The force intensity class. The physical units are force per unit volume, where volume depends on to which manifold the force is applied:

  * force/length^3 (when applied to a 3-D solid),
  * force/length^2 (when applied to a surface),
  * force/length^1 (when applied along a curve), or
  * force/length^0 (when applied at a point).

Signature of the function to compute the value of the force  at any given point `XYZ`, using the columns of the Jacobian matrix of the element, `tangents`, the finite element identifier, `feid`:

```
getforce!(forceout::Vector{CT}, XYZ::Matrix{T}, tangents::Matrix{T}, feid::IT) where {CT, T, IT}
```

A [`DataCache`](@ref) is used to store the data.

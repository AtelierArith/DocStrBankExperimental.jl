```
TemplateReachSet{N, VN, TN<:AbstractDirections{N, VN}, SN<:AbstractVector{N}} <: AbstractLazyReachSet{N}
```

Reach set that stores the support function of a set at a give set of directions.

### Notes

The struct has the following parameters:

  * `N`  – refers to the numerical type of the representation.
  * `VN` – refers to the vector type of the template
  * `TN` – refers to the template type
  * `SN` – vector type that holds the support function evaluations

Concrete subtypes of `AbstractDirections` are defined in the `LazySets` library.

This reach-set implicitly represents a set by a set of directions and support functions. `set(R::TemplateReachSet)` returns a polyhedron in half-space representation.

Apart from the getter functions inherited from the `AbstractReachSet` interface, the following methods are available:

  * `directions(R)`           – return the set of directions normal to the faces of this reach-set
  * `support_functions(R)`    – return the vector of support function evaluations
  * `support_functions(R, i)` – return the `i`-th coordinate of the vector of support function evaluatons

```
@enum Redundancy UNKNOWN_REDUNDANCY LINEARITY_DETECTED NO_REDUNDANCY
```

Redundancy of a H-representation or V-representation.

  * `UNKNOWN_REDUNDANCY`: It is unknown whether there are any undetected linearity or redundancy.
  * `LINEARITY_DETECTED`: There are no undetected linearity.
  * `NO_REDUNDANCY`: There are no undetected linearity not redundancy.

An *undetected linearity* for a V-representation is a [`Line`](@ref) that is implicit in a conic hull of [`Ray`](@ref)s. For instance, `conichull([1, 1], [-1, -1])` has undetected linearity because it contains the [`Line`](@ref) `Line([1, 1])`. Some undetected linearity is less obvious, e.g., `conichull([1, 0, -1], [0, 1, 1], [-1, -1, 0])` contains the [`Line`](@ref) `Line([1, 1, 0])` as the sum of the first two [`Ray`](@ref)s is `Ray([1, 1, 0])`.

An *undetected linearity* for a H-representation is a [`HyperPlane`](@ref) that is implicit in an intersection of [`HalfSpace`](@ref)s. For instance, `HalfSpace([1, 1], 1) ∩ HalfSpace([-1, -1], 1)` has undetected linearity because it contains the [`HyperPlane`](@ref) `HyperPlane([1, 1], 1)`. Some undetected linearity is less obvious, e.g., `HalfSpace([1, 0], -1) ∩ HalfSpace([0, 1], 1) ∩ HalfSpace([-1, -1], 0)` contains the [`HyperPlane`](@ref) `HyperPlane([1, 1], 0)` as the sum of the first two [`HalfSpace`](@ref)s is `HalfSpace([1, 1], 0)`.

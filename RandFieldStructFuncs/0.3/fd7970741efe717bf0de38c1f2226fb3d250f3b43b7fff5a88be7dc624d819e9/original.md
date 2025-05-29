```
AbstractStructFunc{T}
```

is the abstract type of structure functions using floating-point type `T` for their computations.

A structure function `Dᵩ` of a random field `φ` is a callable object such that:

```
Dᵩ(Δr) = ⟨[φ(r + Δr) - φ(r)]^2⟩
```

where `⟨…⟩` denotes expectation while `r` and `Δr` are Cartesian coordinates in units of the grid sampling step.

For sub-types of `AbstractStructFunc{T}`, it is only necessary to implement calling the structure function object with a tuple of coordinates.

```
AbstractSymmetryGroup{T<:AbstractSymmetry}
```

An abstract type representing the set of symmetries of a graph.

## Interface

Any `AbstractSymmetryGroup` type must define methods for `Base` functions `unique`, `iterate`, `length` and `one` such that, for any `s` of type `<: AbstractSymmetryGroup{T}`:

  * `s(i)` is a representative on the symmetry orbit of `i` such that all elements on the orbit share the same representative. The representative should be an integer.
  * `unique(s)` is an iterator over such representatives.
  * iterating over `s` yields the list of symmetry operations `symm`, each represented as an object of type `T` (where `T <:`[`AbstractSymmetry`](@ref) is the parameter to `typeof(s)`). The identity symmetry should not be part of these yielded `symm`, except for the specific [`IncludingIdentity`](@ref) subtype of `AbstractSymmetryGroup`.
  * `one(s)` is the identity symmetry of type `T`.

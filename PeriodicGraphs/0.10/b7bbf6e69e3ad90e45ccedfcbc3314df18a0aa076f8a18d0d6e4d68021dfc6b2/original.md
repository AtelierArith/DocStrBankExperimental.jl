```
abstract type AbstractSymmetry end
```

An abstract type representing a symmetry.

## Interface

Subtypes `T` of `AbstractSymmetry` should implement a method to make their objects `symm` callable on any object upon which the symmetry can act. For example, if `T` represents a symmetry of a 3D embedding of a graph:

  * if `x` represents a 3D point, then `symm(x)` should be the image of that point.
  * if `x` represents a 3D basis of space, then `symm(x)` should be the image of that basis.

When the symmetry is naturally defined on a discrete set of objects, their image should be accessible by indexing on the symmetry. With the same example as before:

  * if `x` is a vertex, `symm[x]` is the image of `x` by the symmetry.
  * if `i` is the integer identifier of vertex `x`, `symm[i]` is the identifier of `symm[x]`.

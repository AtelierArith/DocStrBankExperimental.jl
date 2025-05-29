```
A = LinearMapAA(L::LinearMap ; ...)
```

Constructor for `LinearMapAM`  or `LinearMapAO` given a `LinearMap`.

# Options

  * `prop::NamedTuple = NamedTuple()`; cannot include the fields `_lmap`, `_prop`, `_idim`, `_odim`
  * `T::Type = eltype(L)`
  * `idim::Dims = (size(L,2),)`
  * `odim::Dims = (size(L,1),)`
  * `operator::Bool` by default: `false` if both `idim` & `odim` are 1D.

Output `A` is `LinearMapAO` if `operator` is `true`, else `LinearMapAM`.

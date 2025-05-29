```
DoubleBasis{Tb1<:AbstractBasis, Tb2<:AbstractBasis}
```

Basis for constructing transition matrix from one symmetry sector to another. Note that DoubleBasis can be used as the projector, meaning that it will ignore the symmetry violation. Therefore, extra care is needed when working with this basis.

## Properties:

  * `dgt`: Digits.
  * `B1` : Basis of the target symmetry sector.
  * `B2` : Basis of the starting symmetry sector.
  * `B`  : Base.

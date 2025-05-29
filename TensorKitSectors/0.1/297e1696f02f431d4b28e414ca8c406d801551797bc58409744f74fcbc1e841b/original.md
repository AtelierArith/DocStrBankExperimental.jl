```
abstract type Sector end
```

Abstract type for representing the (isomorphism classes of) simple objects in (unitary and pivotal) (pre-)fusion categories, e.g. the irreducible representations of a finite or compact group. Subtypes `I<:Sector` as the set of labels of a `GradedSpace`.

Every new `I<:Sector` should implement the following methods:

  * `one(::Type{I})`: unit element of `I`
  * `conj(a::I)`: $a̅$, conjugate or dual label of $a$
  * `⊗(a::I, b::I)`: iterable with unique fusion outputs of $a ⊗ b$   (i.e. don't repeat in case of multiplicities)
  * `Nsymbol(a::I, b::I, c::I)`: number of times `c` appears in `a ⊗ b`, i.e. the   multiplicity
  * `FusionStyle(::Type{I})`: `UniqueFusion()`, `SimpleFusion()` or   `GenericFusion()`
  * `BraidingStyle(::Type{I})`: `Bosonic()`, `Fermionic()`, `Anyonic()`, ...
  * `Fsymbol(a::I, b::I, c::I, d::I, e::I, f::I)`: F-symbol: scalar (in case of   `UniqueFusion`/`SimpleFusion`) or matrix (in case of `GenericFusion`)
  * `Rsymbol(a::I, b::I, c::I)`: R-symbol: scalar (in case of   `UniqueFusion`/`SimpleFusion`) or matrix (in case of `GenericFusion`)

and optionally

  * `dim(a::I)`: quantum dimension of sector `a`
  * `frobeniusschur(a::I)`: Frobenius-Schur indicator of `a`
  * `Bsymbol(a::I, b::I, c::I)`: B-symbol: scalar (in case of   `UniqueFusion`/`SimpleFusion`) or matrix (in case of `GenericFusion`)
  * `twist(a::I)` -> twist of sector `a`

Furthermore, `iterate` and `Base.IteratorSize` should be made to work for the singleton type [`SectorValues{I}`](@ref).

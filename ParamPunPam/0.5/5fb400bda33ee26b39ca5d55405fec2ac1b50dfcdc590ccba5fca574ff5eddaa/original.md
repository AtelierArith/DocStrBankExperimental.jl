```
AbstractBlackboxIdeal
```

Blackbox ideals in `K(x)[y]` that can be evaluated at `x`.

## Interface

Subtypes of `AbstractBlackboxIdeal` must implement the following functions:

  * `length(<:AbstractBlackboxIdeal)`: the number of ideal generators.
  * `base_ring(<:AbstractBlackboxIdeal)`: original ground field.
  * `parent(<:AbstractBlackboxIdeal)`: original polynomial ring.
  * `parent_params(<:AbstractBlackboxIdeal)`: original polynomial ring of coefficients.
  * `reduce_mod_p!(<:AbstractBlackboxIdeal, finite_field)`: reduces generators modulo `p`, where `p` is the characteristic of the given `finite_field`.
  * `specialize_mod_p(<:AbstractBlackboxIdeal, point)`: specializes the ideal at `point` and returns the generators of the specialized ideal in Zp[y].

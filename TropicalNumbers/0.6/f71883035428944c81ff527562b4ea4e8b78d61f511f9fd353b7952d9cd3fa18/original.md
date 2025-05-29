```
AbstractSemiring <: Number
```

A [`Semiring`](https://en.wikipedia.org/wiki/Semiring) is a set R equipped with two binary operations + and ⋅, called addition and multiplication, such that:

  * (R, +) is a monoid with identity element called 0;
  * (R, ⋅) is a monoid with identity element called 1;
  * Addition is commutative;
  * Multiplication by the additive identity 0 annihilates ;
  * Multiplication left- and right-distributes over addition;
  * Explicitly stated, (R, +) is a commutative monoid.

[`Tropical number`](https://en.wikipedia.org/wiki/Tropical_geometry) are a set of semiring algebras, described as 

  * (R, +, ⋅, 0, 1).

where R is the set, + and ⋅ are the opeartions and 0, 1 are their identity element, respectively.

In this package, the following tropical algebras are implemented:

  * TropicalAndOr, ([T, F], or, and, false, true);
  * Tropical (TropicalMaxPlus), (ℝ, max, +, -Inf, 0);
  * TropicalMinPlus, (ℝ, min, +, Inf, 0);
  * TropicalMaxMul, (ℝ⁺, max, ⋅, 0, 1).

We implemented fast tropical matrix multiplication in [`TropicalGEMM`](https://github.com/TensorBFS/TropicalGEMM.jl/) and [`CuTropicalGEMM`](https://github.com/ArrogantGao/CuTropicalGEMM.jl/).

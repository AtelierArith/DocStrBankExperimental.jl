```
genus(T::TorQuadModule, signature_pair::Tuple{Int, Int};
                        parity::RationalUnion = modulus_quadratic_form(T))
                                                                -> ZZGenus
```

Return the genus of an integer lattice whose discriminant group has the bilinear form of `T`, the given `signature_pair` and the given `parity`.

The argument `parity` is one of the following: either `parity == 1` for genera of odd lattices, or `parity == 2` for even lattices. By default, `parity` is set to be as the parity of the quadratic form on `T`

If no such genus exists, raise an error.

# Reference

[Nik79](@cite) Corollary 1.9.4 and 1.16.3.

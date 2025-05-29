```
is_genus(T::TorQuadModule, signature_pair::Tuple{Int, Int};
                           parity::RationalUnion = modulus_quadratic_form(T)) -> Bool
```

Return if there is an integral lattice whose discriminant form has the bilinear form of `T`, whose signatures match `signature_pair` and which is of parity `parity`.

The argument `parity` is one of the following: either `parity == 1` for genera of odd lattices, or `parity == 2` for even lattices. By default, `parity` is set to be as the parity of the quadratic form on `T`

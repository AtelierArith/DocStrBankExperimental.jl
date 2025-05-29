```
isogeny_from_kernel_factored(E::EllipticCurve, psi::RingElem) -> Isogeny
```

Compute the isogeny $\phi$: $E$ -> $E'$ where the kernel of $\phi$ contains the points whose $x$-coordinates are roots of the input polynomial $\psi$. Return an array of isogenies whose composition equals the isogeny with the given kernel. The factorisation is determined in the following way: The first maps will purely contain 2-torsion points in the kernel. When there is no 2-torsion left the remaining maps will consist of an isogeny with kernel contained in the p-torsion for every prime divisor p of the degree of the isogeny.

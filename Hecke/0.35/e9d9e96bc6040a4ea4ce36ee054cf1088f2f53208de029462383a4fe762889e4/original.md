```
factor(a::AbsSimpleNumFieldOrderElem) -> Fac{AbsSimpleNumFieldOrderElem}
```

Computes a factorization of $a$ into irreducible elements. The return value is a factorization `fac`, which satisfies `a = unit(fac) * prod(p^e for (p, e) in fac)`.

The function requires that $a$ is non-zero and that all prime ideals containing $a$ are principal, which is for example satisfied if class group of the order of $a$ is trivial.

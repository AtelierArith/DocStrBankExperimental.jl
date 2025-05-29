```
conjugates(x::AbsSimpleNumFieldElem, C::AcbField) -> Vector{AcbFieldElem}
```

Compute the conjugates of $x$ as elements of type `AcbFieldElem`. Recall that we order the complex conjugates $\sigma_{r+1}(x),...,\sigma_{r+2s}(x)$ such that $\sigma_{i}(x) = \overline{\sigma_{i + s}(x)}$ for $r + 1 \leq i \leq r + s$.

Let `p` be the precision of `C`, then every entry $y$ of the vector returned satisfies `radius(real(y)) < 2^-p` and `radius(imag(y)) < 2^-p` respectively.

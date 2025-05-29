```
conjugates(x::AbsSimpleNumFieldElem, abs_tol::Int) -> Vector{AcbFieldElem}
```

Compute the conjugates of $x$ as elements of type `AcbFieldElem`. Recall that we order the complex conjugates $\sigma_{r+1}(x),...,\sigma_{r+2s}(x)$ such that $\sigma_{i}(x) = \overline{\sigma_{i + s}(x)}$ for $r + 1 \leq i \leq r + s$.

Every entry $y$ of the vector returned satisfies `radius(real(y)) < 2^-abs_tol` and `radius(imag(y)) < 2^-abs_tol` respectively.

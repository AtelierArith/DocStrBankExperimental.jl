```
conjugates_arb(x::NumFieldOrderElem, abs_tol::Int) -> Vector{AcbFieldElem}
```

Compute the conjugates of $x$ as elements of type `AcbFieldElem`. Recall that we order the complex conjugates $\sigma_{r+1}(x),...,\sigma_{r+2s}(x)$ such that $\sigma_{i}(x) = \overline{\sigma_{i + s}(x)}$ for $r + 2 \leq i \leq r + s$.

Every entry $y$ of the array returned satisfies `radius(real(y)) < 2^-abs_tol`, `radius(imag(y)) < 2^-abs_tol` respectively.

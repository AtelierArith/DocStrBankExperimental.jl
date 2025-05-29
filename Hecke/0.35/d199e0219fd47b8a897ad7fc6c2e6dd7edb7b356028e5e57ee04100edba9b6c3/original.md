```
saturate(A::SMat{ZZRingElem}) -> SMat{ZZRingElem}
```

Computes the saturation of $A$, that is, a basis for $\mathbf{Q}\otimes M \cap \mathbf{Z}^n$, where $M$ is the row span of $A$ and $n$ the number of rows of $A$.

Equivalently, return $TA$ for an invertible rational matrix $T$, such that $TA$ is integral and the elementary divisors of $TA$ are all trivial.

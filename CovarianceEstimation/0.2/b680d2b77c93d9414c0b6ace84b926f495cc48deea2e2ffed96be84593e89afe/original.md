```
DiagonalCommonVariance
```

Target for linear shrinkage: unit matrix multiplied by average variance of variables. A subtype of `LinearShrinkageTarget` where

  * $F_{ij}=v$ if $i=j$ with $v=\mathrm{tr}(S)/p$ and
  * $F_{ij}=0$ otherwise

```
CommonCovariance
```

Target for linear shrinkage: see `target_C`. A subtype of `LinearShrinkageTarget` where

  * $F_{ij}=v$ if $i=j$ with $v=\mathrm{tr}(S)/p$ and
  * $F_{ij}=c$ with $c=\sum_{i\neq j} S_{ij}/(p(p-1))$ otherwise

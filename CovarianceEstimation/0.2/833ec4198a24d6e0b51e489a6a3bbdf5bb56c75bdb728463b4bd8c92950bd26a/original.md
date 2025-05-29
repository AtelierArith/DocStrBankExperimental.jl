```
ConstantCorrelation
```

Target for linear shrinkage: see `target_F`. A subtype of `LinearShrinkageTarget` where

  * $F_{ij}=S_{ij}$ if $i=j$ and
  * $F_{ij}=\overline{r}\sqrt{S_{ii}S_{jj}}$ otherwise where $\overline{r}$ is the average sample correlation

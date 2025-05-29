```
 fdhinfminus(sys,freq) -> (β, ind, fr)
```

Compute for a stable descriptor system `sys = (A-λE,B,C,D)` the `H∞-` index `β` of its transfer function matrix `G(λ)`. If `freq = missing` (default), then `β` is the  minimum `H∞-norm` of the columns of `G`, `ind` is the index of the minimum-norm column and `fr` is  the frequency where the minimum `H∞-norm` of the columns is achieved. If `freq` is a real value or  a real vector of frequency values, then `β` is the minimum of the 2-norms of the columns of the  frequency responses of `G` evaluated for all values contained in `freq`, `ind` is the index of column  for which the minimum is achieved and `fr` is the corresponding frequency. 

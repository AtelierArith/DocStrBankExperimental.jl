```
 fdhinfmax(sys,freq) -> (γ, ind, fr)
```

Compute for a descriptor system `sys = (A-λE,B,C,D)`, `γ` - the maximum norm of the columns of its transfer function matrix `G(λ)`. If `freq = missing` (default), then `γ` is the  maximum `H∞-norm` of the columns of `G`, `ind` is the index of the maximum-norm column and `fr` is  the frequency where the maximum `H∞-norm` of the columns is achieved. If `freq` is a real value or  a real vector of frequency values, then `γ` is the maximum of the 2-norms of the columns of the  frequency responses of `G` evaluated for all values contained in `freq`, `ind` is the index of column  for which the maximum is achieved and `fr` is the corresponding frequency. 

```
recod_numbyint(x, q)
```

Recode a continuous variable to integers.

  * `x` : Continuous variable (n) to replace.
  * `q` : Numerical values separating classes in `x`.   The first class is labelled to 1.

See examples.

## Examples

```julia
using Jchemo, Statistics
x = [collect(1:10); 8.1 ; 3.1] 

q = [3; 8]
zx = recod_numbyint(x, q)  
[x zx]
probs = [.33; .66]
q = quantile(x, probs) 
zx = recod_numbyint(x, q)  
[x zx]
```

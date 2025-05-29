```
mbconcat()
mbconcat(Xbl)
```

Concatenate horizontaly multiblock X-data.

  * `Xbl` : List of blocks (vector of matrices) of X-data    Typically, output of function `mblock` from (n, p) data.

## Examples

```julia
using Jchemo
n = 5 ; m = 3 ; p = 9 
X = rand(n, p) 
Xnew = rand(m, p)
listbl = [3:4, 1, [6; 8:9]]
Xbl = mblock(X, listbl) 
Xblnew = mblock(Xnew, listbl) 
@head Xbl[3]

model = mbconcat() 
fit!(model, Xbl)
transf(model, Xbl)
transf(model, Xblnew)
```

```
mblock(X, listbl)
```

Make blocks from a matrix.

  * `X` : X-data (n, p).
  * `listbl` : A vector whose each component defines    the colum numbers defining a block in `X`.   The length of `listbl` is the number of blocks.

The function returns a list (vector) of blocks.

## Examples

```julia
using Jchemo
n = 5 ; p = 10 
X = rand(n, p) 
listbl = [3:4, 1, [6; 8:10]]

Xbl = mblock(X, listbl)
Xbl[1]
Xbl[2]
Xbl[3]
```

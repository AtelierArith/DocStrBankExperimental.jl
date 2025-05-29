```julia
randHankel(d, n;  norm )  

randHankel(n;  norm)
```

  * `d` : entry distribution
  * `n` : dimension
  * `norm` : default `false`,  if `norm` set to `true`, then the matrix will be normlaized with $n^{-1/2}$.

# Examples

Generate a $5\times 5$ random Hankel matrix with entries uniformly distributed on $\{1, i, \pi \}$

```julia
randHankel((1,im,pi),5)

5×5 Matrix{Number}:
  1   1  im  1   1
  1  im   1  1   π
 im   1   1  π   π
  1   1   π  π   π
  1   π   π  π  im
```

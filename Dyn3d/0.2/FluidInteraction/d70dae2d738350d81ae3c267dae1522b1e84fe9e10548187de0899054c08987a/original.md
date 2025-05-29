```
DetermineNP(nbody::Int, Δx)
```

Run this function before running GenerateBodyGrid, to determine number of points on a 2d body, in order to satisfy the desired number of points on the 1d body.

np = (# of points on 1d plate - 1)*4+1. So np=201 has 51 points(1 body), np=101 has 26 points(2 body), np=49 has 13 points(4 body), np=25 has 7 points(8 body), etc.

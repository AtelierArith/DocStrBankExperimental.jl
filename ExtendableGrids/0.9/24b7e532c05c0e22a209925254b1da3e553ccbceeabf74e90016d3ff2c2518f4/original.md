```
c=glue(a,b)
```

Glue together two vectors `a` and b resulting in a vector c. They last element  of `a` shall be equal (up to tol) to the first element of b. The result fulfills `length(c)=length(a)+length(b)-1`

```
sum_losses(lArray::Array{T,1}, p0) where T <: Function
```

  * Given array of cost functions c1...cn, makes new cost function D. Multithreads evaluation of D(p) and D(p,g) if threads are available.
  * c1...cn must be differentiable: ci(p,g) returns cost and mutates gradient g

D(p) = sum*i c*i(p) D(p,g) mutates g to give gradient of D. 

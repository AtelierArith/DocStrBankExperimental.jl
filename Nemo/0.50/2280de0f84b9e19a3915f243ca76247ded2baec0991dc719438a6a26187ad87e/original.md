```
lindep(A::Vector{AcbFieldElem}, bits::Int)
```

Find a small linear combination of the entries of the array $A$ that is small (using LLL). The entries are first scaled by the given number of bits before truncating the real and imaginary parts to integers for use in LLL. This function can be used to find linear dependence between a list of complex numbers. The algorithm is heuristic only and returns an array of Nemo integers representing the linear combination.

```
lindep(A::Matrix{ComplexFieldElem}, bits::Int)
```

Find a (common) small linear combination of the entries in each row of the array $A$, that is small (using LLL). It is assumed that the complex numbers in each row of the array share the same linear combination. The entries are first scaled by the given number of bits before truncating the real and imaginary parts to integers for use in LLL. This function can be used to find a common linear dependence shared across a number of lists of complex numbers. The algorithm is heuristic only and returns an array of Nemo integers representing the common linear combination.

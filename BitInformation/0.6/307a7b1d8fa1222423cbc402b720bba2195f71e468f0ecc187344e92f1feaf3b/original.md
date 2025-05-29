```
H = bitpattern_entropy(A::AbstractArray,base::Real=2)
```

Calculates the bit pattern entropy `H` for an array `A` by reinterpreting the elements as UInts and sorting them to avoid creating a histogram. The bit pattern entropy is the entropy from occurences of every possible bitpattern in `T` in elements of `A`. The unit of entropy is given by base `base`, such that for the default `base=2` it is bits.

```
bitarray(v::Vector, [nbits::Int]) -> BitArray
bitarray(v::Int, nbits::Int) -> BitArray
bitarray(nbits::Int) -> Function
```

Construct BitArray from an integer vector, if nbits not supplied, it is 64. If an integer is supplied, it returns a function mapping a Vector/Int to bitarray.

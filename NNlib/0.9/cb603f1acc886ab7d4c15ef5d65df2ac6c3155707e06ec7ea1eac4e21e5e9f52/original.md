```
pad_zeros(x, pad::Tuple; [dims])
pad_zeros(x, pad::Int; [dims])
```

Pad the array `x` with zeros. Equivalent to [`pad_constant`](@ref) with the constant equal to 0. 

```
mince(x::IntervalBox, ncuts::::NTuple{N,Int})
```

`x[i]`を`ncuts[i]`の区間に分割します。これらの区間は、すべての可能な`IntervalBox`に結合され、ベクトルとして返されます。

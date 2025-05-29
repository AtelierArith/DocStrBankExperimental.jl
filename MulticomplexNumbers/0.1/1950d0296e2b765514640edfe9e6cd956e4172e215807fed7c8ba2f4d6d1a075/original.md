```
ascomplex(A::AbstractArray{M})
```

Returns a view of the multicomplex input array A as an array of complex numbers, mapping i⁽¹⁾ -> im

If A has size (m, n, ...) with multicomplex numbers of dimension N, then the output will have size (2^(N-1), m, n, ...).

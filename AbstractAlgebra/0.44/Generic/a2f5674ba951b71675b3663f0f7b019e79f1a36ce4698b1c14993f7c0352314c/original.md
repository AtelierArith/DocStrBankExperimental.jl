```
mul_karatsuba(a::Poly{T}, b::Poly{T}, cutoff::Int) where T <: RingElement
```

Return $a \times b$ using the Karatsuba algorithm recursively for problems of size roughly greater than `cutoff`.

```
mullow_karatsuba(a::Poly{T}, b::Poly{T}, n::Int, cutoff::Int) where T <: RingElement
```

Return $a \times b$ truncated to $n$ terms using the Karatsuba algorithm recursively for problems of size roughly greater than `cutoff`.

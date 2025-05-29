```
input_resolvent(sys::AbstractStateSpace)
```

Return the input-mapped resolvent of `sys`

$$
(sI - A)^{-1}B
$$

i.e., the system `ss(A, B, I, 0)`.

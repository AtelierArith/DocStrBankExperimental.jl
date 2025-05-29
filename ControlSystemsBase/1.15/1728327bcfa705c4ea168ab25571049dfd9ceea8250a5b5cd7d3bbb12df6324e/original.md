```
resolvent(sys::AbstractStateSpace)
```

Return the resolvent of `sys`

$$
(sI - A)^{-1}
$$

i.e., the system `ss(A, I, I, 0)`.

See also [`input_resolvent`](@ref).

```
resolvent(sys::AbstractStateSpace)
```

`sys`の解決子を返します

$$
(sI - A)^{-1}
$$

すなわち、システム `ss(A, I, I, 0)`。

[`input_resolvent`](@ref) も参照してください。

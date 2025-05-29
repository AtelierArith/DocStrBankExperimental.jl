```
input_resolvent(sys::AbstractStateSpace)
```

システム `sys` の入力マッピングされた解決策を返します

$$
(sI - A)^{-1}B
$$

すなわち、システム `ss(A, B, I, 0)`。

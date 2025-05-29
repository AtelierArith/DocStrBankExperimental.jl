```
μobs, μexp = linearization_test(F, mₒ; μ)
```

Thest that the jacobian, `J`, of `F` satisfies the Taylor expansion:

`F(m) = F(m_o) + F'(m_o)δm + O(δm^2)`

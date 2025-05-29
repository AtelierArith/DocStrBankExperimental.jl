```
find_start_pair(F; max_tries = 100, atol = 0.0, rtol = 1e-12)
```

Try to find a pair `(x,p)` for the system `F` such that `F(x,p) = 0` by randomly sampling a pair `(x₀, p₀)` and performing Newton's method in variable *and* parameter space.

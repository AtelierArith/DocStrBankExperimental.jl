```
optimize!(fdf, M::Wrapper, x0)
```

Find an optimizer for `fdf`, starting with the initial approximation `x0`. `fdf(x, g)` must return a tuple (f(x), ∇f(x)) and, if `g` is mutable, overwrite it with the gradient.

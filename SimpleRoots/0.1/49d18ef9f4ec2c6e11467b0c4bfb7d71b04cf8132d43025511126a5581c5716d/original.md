```
findzero(f, method::Brent, atol, maxiter)
findzero(f, method::Brent; atol=1e-7, max_iter=100)
```

Find root using Brents method. Returns a tuple of the found value and a Bool specifying wether the root was found within the tolerance, or not.

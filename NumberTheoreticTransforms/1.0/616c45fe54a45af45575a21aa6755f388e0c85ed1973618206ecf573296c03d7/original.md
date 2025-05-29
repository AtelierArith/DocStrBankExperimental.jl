```
modfermat(n, q)
```

Equivalent of mod(n, q) but uses faster algorithm. Constraints:

  * `q` must be a Fermat number $ 2^{2^t}+1 $
  * `n` must be smaller or equal to $ (q-1)^2 $
  * `n` must be grater or equal to $ 0 $

If above constraints are not met, the result is undefined.

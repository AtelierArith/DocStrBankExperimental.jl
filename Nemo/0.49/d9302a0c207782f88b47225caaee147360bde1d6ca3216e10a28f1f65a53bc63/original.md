```
frobenius(x::FqPolyRepFieldElem, n = 1)
```

Return the iterated Frobenius $\sigma_p^n(x)$ where $\sigma_p$ is the Frobenius map sending the element $a$ to $a^p$ in the finite field of characteristic $p$. By default the Frobenius map is applied $n = 1$ times if $n$ is not specified.

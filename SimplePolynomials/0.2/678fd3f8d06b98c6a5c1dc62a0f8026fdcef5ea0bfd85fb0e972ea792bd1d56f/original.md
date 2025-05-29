`getx()` is a convenient way to create `SimplePolynomial(0,1)`. Typical use:

```
x = getx()
p = 2 + x - 3*x^2
```

Use `getx(T)` for coefficients of type `T`, e.g., `getx(Mod{13})`.

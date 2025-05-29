```
f, g = objgrad!(nlp, x, g)
```

Evaluate $f(x)$ and $∇f(x)$ at `x`. `g` is overwritten with the value of $∇f(x)$.

```
ChainedLinear(X::NEAT, Y::NEAT)
```

Equate 2 tests in a chain through the common test scores. Now supports only 2 form equating.

# Basic Algorithm

1. put X on the scale of V -call lV(x);
2. put V on the scale of Y - call lY(v);
3. obtain Y-equivalent as lY(x).

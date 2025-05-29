```
f1(M::ConfusionMatrix)
```

F₁ score, defined as the harmonic mean between precision and recall:

$2\times\frac{PPV\times TPR}{PPV + TPR}$

This uses the more general `fscore` internally.

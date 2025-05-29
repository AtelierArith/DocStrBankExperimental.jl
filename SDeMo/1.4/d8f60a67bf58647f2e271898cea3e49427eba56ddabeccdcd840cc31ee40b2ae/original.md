```
fscore(M::ConfusionMatrix, β=1.0)
```

Fᵦ score, defined as the harmonic mean between precision and recall, using a positive factor β indicating the relative importance of recall over precision:

$(1 + \beta^2)\times\frac{PPV\times TPR}{(\beta^2 \times PPV) + TPR}$

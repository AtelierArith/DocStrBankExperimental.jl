```
tropicalpolynomial(p::MP.AbstractPolynomial)
```

Interprets a normal polynomials a tropical one. This will especially convert all coefficents which are 1 (neutral element w.r.t. multiplication) to 0 (neutral element wr.t. tropical multiplication).

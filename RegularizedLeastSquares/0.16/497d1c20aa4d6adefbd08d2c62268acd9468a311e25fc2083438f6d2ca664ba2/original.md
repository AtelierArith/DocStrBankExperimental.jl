```
prox!(reg::TVRegularization, x, λ)
```

Proximal map for TV regularization. Calculated with the Condat algorithm if the TV is calculated only along one dimension and with the Fast Gradient Projection algorithm otherwise.

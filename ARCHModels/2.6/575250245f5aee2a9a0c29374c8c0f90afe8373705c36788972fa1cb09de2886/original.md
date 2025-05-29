```
predict(am::MultivariateARCHModel, what=:covariance)
```

Form a 1-step ahead prediction from `am`. `what` controls which object is predicted. The choices are `:covariance` (the default) or `:correlation`.

```
emit(temperature :: Real, emission :: Emission)
```

Calculates the right-hand side of the boundary conditions for a given `Emission`.

$$
\Phi = -h ~ (\theta - \theta_{amb}) - \sigma ~ [\varepsilon_{1} ~ \theta^4 - \varepsilon_{2} ~ \theta_{amb}^4)]
$$

```
NRMSE(obs,sim)
```

Returns the Normalized Root Mean Squared Error between observations `obs` and simulations `sim`. Normalization is performed using division by observations range (max-min).

# Examples

```@example
using PlantSimEngine

obs = [1.0, 2.0, 3.0]
sim = [1.1, 2.1, 3.1]

NRMSE(obs, sim)
```

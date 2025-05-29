```
RMSE(obs,sim)
```

Returns the Root Mean Squared Error between observations `obs` and simulations `sim`.

The closer to 0 the better.

# Examples

```@example
using PlantSimEngine

obs = [1.0, 2.0, 3.0]
sim = [1.1, 2.1, 3.1]

RMSE(obs, sim)
```

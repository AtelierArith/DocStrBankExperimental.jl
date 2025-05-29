```
EF(obs,sim)
```

Returns the Efficiency Factor between observations `obs` and simulations `sim` using NSE (Nash-Sutcliffe efficiency) model. More information can be found at https://en.wikipedia.org/wiki/Nash%E2%80%93Sutcliffe*model*efficiency_coefficient.

The closer to 1 the better.

# Examples

```@example
using PlantSimEngine

obs = [1.0, 2.0, 3.0]
sim = [1.1, 2.1, 3.1]

EF(obs, sim)
```

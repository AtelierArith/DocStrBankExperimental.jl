```
dr(obs,sim)
```

Returns the Willmott’s refined index of agreement dᵣ. Willmot et al. 2011. A refined index of model performance. https://rmets.onlinelibrary.wiley.com/doi/10.1002/joc.2419

The closer to 1 the better.

# Examples

```@example
using PlantSimEngine

obs = [1.0, 2.0, 3.0]
sim = [1.1, 2.1, 3.1]

dr(obs, sim)
```

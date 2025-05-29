```
dr(obs,sim)
```

Willmottの洗練された一致指数dᵣを返します。Willmot et al. 2011. モデル性能の洗練された指標。 https://rmets.onlinelibrary.wiley.com/doi/10.1002/joc.2419

1に近いほど良いです。

# 例

```@example
using PlantSimEngine

obs = [1.0, 2.0, 3.0]
sim = [1.1, 2.1, 3.1]

dr(obs, sim)
```

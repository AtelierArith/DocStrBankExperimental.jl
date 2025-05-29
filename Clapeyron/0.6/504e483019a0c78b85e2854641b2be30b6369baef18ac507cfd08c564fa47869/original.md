```
eutectic_point(model::CompositeModel, p)
```

Calculates the eutectic point of a binary mixture (at a given pressure). Returns a tuple containing the eutectic temperature and the composition at the eutectic point.

Can only function when solid and liquid models are specified within a CompositeModel.

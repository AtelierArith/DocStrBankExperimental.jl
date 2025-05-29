```
momentum!(dict,bd)
```

  * `dict` : structure of terms in the energy conservation. Includes keys of    "mlag", "mlag*temp", "mgra", "mgra*temp", "mkin"
  * `bd` : current BodyDyn structure

Computes total body's momentum in inertia frame. This function only needs to be called once at the end stage in RK scheme.

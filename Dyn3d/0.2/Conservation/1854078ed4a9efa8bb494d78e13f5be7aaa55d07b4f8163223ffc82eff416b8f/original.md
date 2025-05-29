```
energy!(dict,bd,k)
```

  * `dict` : structure of terms in the energy conservation. Includes keys of   "edam", "edam*temp", "elag", "elag*temp", "ekin", "espr", "egra"
  * `bd` : current BodyDyn structure

For the current joint-body connection, computes kinetic energy, spring potential energy and gravitational potential energy. This function only needs to be called once at the end stage in RK scheme.

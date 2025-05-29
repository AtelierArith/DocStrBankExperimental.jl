```
modeshape(model::Plate, kpq, x, y)
modeshape(model::Membrane, kpq, x, y)
```

Computes the mass-normalized mode shapes of a simply supported rectangular plate or a clamped rectangular membrane

**Inputs**

  * `model`: Structure containing the data related to the structure
  * `kmn`: Matrix of modal wave numbers
  * `(x, y)`: Coordinates of the points where the mode shapes are calculated

**Output**

  * `ϕ`: Mass-normalized mode shapes

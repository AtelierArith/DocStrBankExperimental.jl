```
SystemWithOutput{ST<:AbstractSystem, MT<:AbstractMap} <: AbstractSystem
```

Parametric composite type for systems with outputs. It is parameterized in the system's type (`ST`) and in the map's type (`MT`).

### Fields

  * `s`         – system of type `ST`
  * `outputmap` – output map of type `MT`

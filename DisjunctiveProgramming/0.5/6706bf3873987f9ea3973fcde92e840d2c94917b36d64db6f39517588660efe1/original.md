```
GDPModel([optimizer]; [kwargs...])::JuMP.Model

GDPModel{T}([optimizer]; [kwargs...])::JuMP.GenericModel{T}

GDPModel{M <: JuMP.AbstractModel, VrefType, CrefType}([optimizer], [args...]; [kwargs...])::M
```

The core model object for building general disjunction programming models.

```
Prox
```

An optimizer attribute for specifying a prox policy to be used in the quasi-gradient algorithm. Options are:

  * [`NoProx`](@ref): Unconstrained.
  * [`Polyhedron`](@ref): QP projection on polyhedral space ?PolyhedronProjection for parameter descriptions. (default)
  * [`AndersonAcceleration`](@ref):  Anderson acceleration of inner prox step ?AndersonAcceleratedProximal for parameter descriptions.
  * [`Nesterov`](@ref):  Nesterov acceleration of inner prox step ?NesterovProximal for parameter descriptions.
  * [`DryFriction`](@ref):  Dry-friction acceleration of inner prox step ?DryFrictionProximal for parameter descriptions.

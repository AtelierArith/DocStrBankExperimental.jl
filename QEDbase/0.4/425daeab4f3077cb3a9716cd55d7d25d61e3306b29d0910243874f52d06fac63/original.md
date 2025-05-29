Abstract base type for all compute model definitions in the context of scattering processes. Every subtype of `AbstractModelDefinition` is associated with a fundamental interaction. Therefore, one needs to implement the following soft interface function

```Julia
fundamental_interaction_type(::AbstractModelDefinition)
```

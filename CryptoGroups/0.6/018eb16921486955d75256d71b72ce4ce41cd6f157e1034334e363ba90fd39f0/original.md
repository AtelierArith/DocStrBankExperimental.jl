```
concretize_type(::Type{T}, args...) <: T where T
```

Constructs a concrete subtype of union all or abstract type `T`. The arguments `args` are used to set concrtete values for type parameters of `T`, effectivelly `concretizing` a generic abstract type. The resulting type then can be instanitated by a value. 

See also `spec`

```
DebugGroup <: DebugAction
```

group a set of [`DebugAction`](@ref)s into one action, where the internal prints are removed by default and the resulting strings are concatenated

# Constructor

```
DebugGroup(g)
```

construct a group consisting of an Array of [`DebugAction`](@ref)s `g`, that are evaluated `en bloque`; the method does not perform any print itself, but relies on the internal prints. It still concatenates the result and returns the complete string

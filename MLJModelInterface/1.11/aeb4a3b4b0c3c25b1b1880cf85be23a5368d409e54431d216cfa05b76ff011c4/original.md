```
is_same_except(m1, m2, exceptions::Symbol...; deep_properties=Symbol[])
```

If both `m1` and `m2` are of `MLJType`, return `true` if the following conditions all hold, and `false` otherwise:

  * `typeof(m1) === typeof(m2)`
  * `propertynames(m1) === propertynames(m2)`
  * with the exception of properties listed as `exceptions` or bound to an `AbstractRNG`, each pair of corresponding property values is either "equal" or both undefined. (If a property appears as a `propertyname` but not a `fieldname`, it is deemed as always defined.)

The meaining of "equal" depends on the type of the property value:

  * values that are themselves of `MLJType` are "equal" if they are equal in the sense of `is_same_except` with no exceptions.
  * values that are not of `MLJType` are "equal" if they are `==`.

In the special case of a "deep" property, "equal" has a different meaning; see [`deep_properties`](@ref)) for details.

If `m1` or `m2` are not `MLJType` objects, then return `==(m1, m2)`.

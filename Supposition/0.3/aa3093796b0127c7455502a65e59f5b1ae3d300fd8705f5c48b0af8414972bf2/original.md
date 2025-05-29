```
event!(obj)
event!(label::AbstractString, obj)
```

Record `obj` as an event in the current testcase that occured while running your property. If no `label` is given, a default one will be chosen.

!!! warning "Callability"
    This can only be called while a testcase is currently being examined or an example for a `Possibility` is being actively generated. It is ok to call this inside of `@composed` or `@check`, as well as any functions only intended to be called from one of those places.


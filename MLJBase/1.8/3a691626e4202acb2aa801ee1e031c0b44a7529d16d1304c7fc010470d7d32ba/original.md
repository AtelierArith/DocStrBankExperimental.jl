```
@constant x = value
```

Private method (used in testing).

Equivalent to `const x = value` but registers the binding thus:

```julia
MLJBase.HANDLE_GIVEN_ID[objectid(value)] = :x
```

Registered objects get displayed using the variable name to which it was bound in calls to `show(x)`, etc.

!!! warning
    As with any `const` declaration, binding `x` to new value of the same type is not prevented and the registration will not be updated.


```
    LabelNumeral(s::String; prefix="", caselower=false) --> LabelNumeral{Int}
```

Specialized constructor to return a LabelNumeral{Int} type.

Example:

```
julia> a = LabelNumeral("23"; prefix="A-", caselower=true)
A-23
```

The `prefix` does not get affected by the `caselower` parameter.

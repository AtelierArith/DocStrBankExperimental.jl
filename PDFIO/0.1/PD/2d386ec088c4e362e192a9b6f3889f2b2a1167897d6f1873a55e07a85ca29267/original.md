```
    pdDocClose(doc::PDDoc, num::Int) -> Nothing
```

Reclaim the resources associated with a `PDDoc` object. Once called the `PDDoc` object cannot be further used.

# Example

```
julia> pdDocClose(doc)
```

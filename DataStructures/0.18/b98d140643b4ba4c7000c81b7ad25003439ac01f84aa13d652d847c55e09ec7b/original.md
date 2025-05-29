```
SortedDict(d, o=Forward)
```

and `SortedDict{K,V}(d, o=Forward)`

Construct a `SortedDict` from an ordinary Julia dict `d` (or any associative type), e.g.:

```julia
d = Dict("New York" => 1788, "Illinois" => 1818)
c = SortedDict(d)
```

In this example the key-type is deduced to be `String`, while the value-type is `Int`.

If `K` and `V` are not specified, the key type and value type are inferred from the given dictionary. The ordering object `o` defaults to `Forward`.

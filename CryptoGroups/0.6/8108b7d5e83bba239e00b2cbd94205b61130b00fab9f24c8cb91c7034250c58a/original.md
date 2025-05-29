```
abstract type Group end
```

A cyclic group interface type. It is expected that constructor of the group does instance validation and throws an `ArgumentError` if it can't be constructed. Identity element can be constructed with explicit argument `allow_one=true` and validation can be opted out with `skip_validation=true` argument for the constructor which can be useful for deserialization from a secure location locally. 

The group element shall support construction from vector of bytes (octet) as well as `octet` method itself. In addition `value` method is expected that provides most simple representation useful for debugging purposes. Given `g::Group` a following constructor methods are supported:

```julia
G = typeof(g)
g == G(octet(g)) == G(value(g))
one(G) == G(octet(one(G)), allow_one=true)
```

The group must support `order`, `*`, `^`, `rem` and identity element via `one`. For concrete implementations see `PGroup` and `ECGroup`. 

```
parse_tor_struct(s::AbstractString) -> t::NamedTuple
```

The input string is an entry in a `TorObj` `propval` field, consisting of, e.g., "struct(status: automatic, x: 1 in, y:23.4  mm)".  This function parses out the Ticra struct and returns a `NamedTuple` `t` whose `propertynames` are the Ticra struct field names.  The `values` of `t` are either strings or `Unitful` quantities.  In the example given, `t.status == "automatic"`, `t.x == 1.0u"inch"`, and  `t.y == 23.4u"mm"`.

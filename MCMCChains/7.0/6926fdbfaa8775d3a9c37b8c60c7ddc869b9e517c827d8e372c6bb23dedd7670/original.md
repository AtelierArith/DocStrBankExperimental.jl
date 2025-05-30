```
Chains
```

Parameters:

  * `value`: An `AxisArray` object with axes `iter` × `var` × `chains`
  * `logevidence` : A field containing the logevidence.
  * `name_map` : A `NamedTuple` mapping each variable to a section.
  * `info` : A `NamedTuple` containing miscellaneous information relevant to the chain.

The `info` field can be set using `setinfo(c::Chains, n::NamedTuple)`.

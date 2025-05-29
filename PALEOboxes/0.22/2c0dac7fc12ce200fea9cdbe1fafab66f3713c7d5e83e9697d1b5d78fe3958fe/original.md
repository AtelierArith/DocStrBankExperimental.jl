```
VarList_namedtuple(varcollection; components=false) -> VarList_namedtuple
```

Create a `VarList_namedtuple` describing a collection of `VariableReaction`s, `create_accessors` will then return a NamedTuple with field names = `VariableReaction.localname` and field values = corresponding data arrays.

If `components = true`, each NamedTuple field will be a Vector of data array components.

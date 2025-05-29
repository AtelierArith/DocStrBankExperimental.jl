```
VarList_namedtuple_fields(objectwithvars; components=false) -> VarList_namedtuple
```

Create a `VarList_namedtuple` describing `VariableReaction` fields in `objectwithvars`, `create_accessors` will then return a NamedTuple with field names = field names in `objectwithvars` and field values = corresponding data arrays.

If `components = true`, each NamedTuple field will be a Vector of data array components.

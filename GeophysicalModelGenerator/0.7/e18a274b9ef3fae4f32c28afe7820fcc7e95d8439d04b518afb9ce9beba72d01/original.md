```
V = addfield(V::FEData,new_fields::NamedTuple; cellfield=false)
```

Add `new_fields` fields to a `FEData` dataset; set `cellfield` to `true` if the field is a cell field; otherwise it is a vertex field

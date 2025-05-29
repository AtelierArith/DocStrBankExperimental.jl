```
V = addfield(V::Q1Data,new_fields::NamedTuple; cellfield=false)
```

Add `new_fields` fields to a `Q1Data` dataset; set `cellfield` to `true` if the field is a cell field; otherwise it is a vertex field

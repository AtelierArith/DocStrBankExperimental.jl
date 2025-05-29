```
resolve(collection::DataCollection, ident::Identifier;
        resolvetype::Bool=true, requirematch::Bool=true)
```

Attempt to resolve an identifier (`ident`) to a particular data set. Matching data sets will searched for from `collection`.

When `resolvetype` is set and `ident` specifies a datatype, the identified data set will be read to that type.

When `requirematch` is set an error is raised should no dataset match `ident`. Otherwise, `nothing` is returned.

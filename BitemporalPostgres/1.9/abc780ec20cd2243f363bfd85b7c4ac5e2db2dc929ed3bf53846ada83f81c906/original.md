get_revision(rtype::Type{RT}, cid::DbId, vid::DbId) where {RT<:ComponentRevision}

```
retrieves the revision of component cid as of version vid 
the revision must exist
```

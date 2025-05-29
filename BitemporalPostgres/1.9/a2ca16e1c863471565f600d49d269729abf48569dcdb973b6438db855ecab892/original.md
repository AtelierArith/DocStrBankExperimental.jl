get_revision(ctype::Type{CT}, rtype::Type{RT}, hid::DbId, vid::DbId) where {CT<:Component,RT<:ComponentRevision}

```
retrieves the revision of the unique component of type CT in history hid as of version vid 
the revision must exist
```

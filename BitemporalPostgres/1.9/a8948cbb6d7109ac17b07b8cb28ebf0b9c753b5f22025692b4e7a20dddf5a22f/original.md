function get_revisionIfAny(rtype::Type{RT}, hid::DbId, vid::DbId, )::Vector{RT} where {RT<:ComponentRevision}     retrieves the revision of component cid if one exists as of version vid 

```
An optional component may have a revision for a version later as vid. In such cases a component w/o valid revision is itself valid, just to be ignored for the current version.
```

function get_revisionIfAny( ctype::Type{CT}, rtype::Type{RT}, hid::DbId, vid::DbId, )::Vector{RT} where {CT<:Component,RT<:ComponentRevision}     retrieves the revision of the unique component of type CT in history hid if one exists as of version vid 

```
An optional (unique) component may have a revision for a version later as vid. In such cases a component w/o valid revision is itself valid, just to be ignored for the current version.
```

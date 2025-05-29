```
from_name(container::Supervised, name::AbstractString)
```

Return the process identified by `name` that is supervised by `container` or nothing if such process does not exists.

It may be useful in case the process name contains dots because it does not lookup the supervision hierarchy using the dot as separator between nodes.

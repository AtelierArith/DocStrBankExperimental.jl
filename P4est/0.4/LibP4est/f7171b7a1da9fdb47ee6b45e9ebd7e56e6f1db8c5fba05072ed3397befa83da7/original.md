```
p4est_connect_type_t
```

Characterize a type of adjacency.

Several functions involve relationships between neighboring trees and/or quadrants, and their behavior depends on how one defines adjacency: 1) entities are adjacent if they share a face, or 2) entities are adjacent if they share a face or corner. [`p4est_connect_type_t`](@ref) is used to choose the desired behavior. This enum must fit into an int8_t.

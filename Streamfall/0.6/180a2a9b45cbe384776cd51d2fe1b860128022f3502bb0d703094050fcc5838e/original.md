```
create_node(mg::MetaDiGraph, node_name::String, details::AbstractDict, nid::Int)
```

Create a node specified with given name (if it does not exist).

Returns

  * `this_id` : ID of node (if pre-existing) and
  * `nid` : incremented node id for entire network (equal to `this_id` if exists)

```
locatefirst(name, attribute, value, node) -> Node
```

Finds first node with `name` which has an `attribute` with `value`. E.g. to locate a node `<egg foobar="spam"/>` you could write:     locatefirst("egg", "foobar", "spam", parent_node)

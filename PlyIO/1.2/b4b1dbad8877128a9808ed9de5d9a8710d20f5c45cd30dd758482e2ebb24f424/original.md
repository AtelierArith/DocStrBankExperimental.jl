```
PlyElement(name, [len | props...])
```

Construct a ply `element $name $len`, containing a list of properties with a name which can be retrieved using `plyname`.  Properties can be accessed with the array interface, or looked up by indexing with a string.

The expected length `len` is used if it is set, otherwise the length shared by the property vectors is used.

```
cscreate(containers[; optional keyword arguments...])
```

Create a new CloudSeis dataset without creating a corresponding handle and without opening the data-set.  Please see help for `csopen` for the `optional keyword arguments`.

`containers` is either of type `Container` or `Vector{<:Container}`.  In the former case, all extents are stored in a single container, and in the later case, extents are sharded accross multiple containers.

In "r" and "r+" mode, and when the existing data-set is sharded over multiple containers, it is only required to supply the primary container.  The "description.json" object is in the "primary" container.

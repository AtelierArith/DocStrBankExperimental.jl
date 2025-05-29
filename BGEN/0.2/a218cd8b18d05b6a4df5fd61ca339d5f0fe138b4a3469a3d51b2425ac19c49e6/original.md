```
iterator(b::Bgen; offsets=nothing, from_bgen_start=nothing)
```

Retrieve a variant iterator for `b`.

  * If `offsets` is provided, or `.bgen.bgi` is provided and

`from_bgen_start` is `false`, it returns a `VariantIteratorFromOffsets`, iterating over the list of offsets.

  * Otherwise, it returns a `VariantIteratorFromStart`, iterating from the start

of bgen file to the end of it sequentially.

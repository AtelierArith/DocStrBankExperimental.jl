```
sc_mstamp
```

A data container to create memory items of the same size. Allocations are bundled so it's fast for small memory sizes. The items created will remain valid until the container is destroyed. There is no option to return an item to the container. See sc*mempool*t for that purpose.

| Field      | Note                           |
|:---------- |:------------------------------ |
| elem_size  | Input parameter: size per item |
| per_stamp  | Number of items per stamp      |
| stamp_size | Bytes allocated in a stamp     |
| cur_snext  | Next number within a stamp     |
| current    | Memory of current stamp        |
| remember   | Collects all stamps            |

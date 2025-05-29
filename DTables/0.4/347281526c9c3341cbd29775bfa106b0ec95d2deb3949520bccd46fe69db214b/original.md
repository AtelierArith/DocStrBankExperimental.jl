```
DTable
```

Structure representing the distributed table based on Dagger.

The table is stored as a vector of `Chunk` structures which hold partitions of the table. That vector can also store `Dagger.EagerThunk` structures when an operation that modifies the underlying partitions was applied to it (currently only `filter`).

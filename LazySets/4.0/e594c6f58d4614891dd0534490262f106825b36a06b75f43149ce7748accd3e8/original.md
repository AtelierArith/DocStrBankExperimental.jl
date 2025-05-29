```
singleton_list(P::LazySet)
```

Return the vertices of a polytopic set as a list of singletons.

### Input

  * `P` – polytopic set

### Output

A list of the vertices of `P` as `Singleton`s.

### Notes

This function relies on `vertices_list`, which raises an error if the set is not polytopic (e.g., unbounded).

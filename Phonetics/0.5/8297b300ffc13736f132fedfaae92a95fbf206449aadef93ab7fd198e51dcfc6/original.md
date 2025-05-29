```
pnd(corpus::Array, queries::Array; [progress=true])
```

Calculate the phonological neighborhood density (pnd) for each item in `queries` based on the items in `corpus`. This function uses a vantage point tree data structure to speed up the search for neighbors by pruning the search space. This function should work regardless of whether the items in `queries` are in `corpus` or not.

# Parameters

  * **corpus** The corpus to be queried for phonological neighbors
  * **queries** The items to query phonological neighbors for in `corpus`
  * **progress** Whether to display a progress meter or not

# Returns

  * A `DataFrame` with the queries in the first column and the phonological   neighborhood density in the second

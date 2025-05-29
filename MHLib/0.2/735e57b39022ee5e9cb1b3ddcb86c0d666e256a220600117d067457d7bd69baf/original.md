```
SubsetVectorSolution{T}
```

A type for solutions that are arbitrary cardinality subsets of a given set.

Represented in vector form. The front part represents the selected elements, the back part optionally the unselected ones.

A concrete type must implement the following:

  * `x`: Vector of different elements, first the selected ones, then optionally the not   selected ones.
  * `sel`: Integer indicating the number of selected elements
  * `all_elements(solution)`: complete set of which a subset shall be selected;   only needed if unselected elements are not maintained behind the selected ones

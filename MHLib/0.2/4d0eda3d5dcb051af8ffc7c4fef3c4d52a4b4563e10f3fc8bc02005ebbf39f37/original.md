```
all_elements(::SubsetVectorSolution)
```

Return a set with all elements.

Needs to be defined in a concrete type if the unselected elements are not stored in `x` behind the selected ones, i.e., when `unselected_elems_in_x==true`.

```
p4est_split_array(array, level, indices)
```

Split an array of quadrants by the children of an ancestor.

Given a sorted **array** of quadrants that have a common ancestor at level **level**, compute the **indices** of the first quadrant in each of the common ancestor's children at level **level** + 1.

### Parameters

  * `array`:[in] The sorted array of quadrants of level > **level**.
  * `level`:[in] The level at which there is a common ancestor.
  * `indices`:[in,out] The indices of the first quadrant in each of the ancestors's children, plus an additional index on the end. The quadrants of **array** that are descendants of child i have indices between indices[i] and indices[i + 1] - 1. If indices[i] = indices[i+1], this indicates that no quadrant in the array is contained in child i.

### Prototype

```c
void p4est_split_array (sc_array_t * array, int level, size_t indices[]);
```

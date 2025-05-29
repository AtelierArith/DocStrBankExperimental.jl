```
p4est_find_range_boundaries(lq, uq, level, faces, corners)
```

Find the boundary points touched by a range of quadrants.

Given two smallest quadrants, **lq** and **uq**, that mark the first and the last quadrant in a range of quadrants, determine which portions of the tree boundary the range touches.

### Parameters

  * `lq`:[in] The smallest quadrant at the start of the range: if NULL, the tree's first quadrant is taken to be the start of the range.
  * `uq`:[in] The smallest quadrant at the end of the range: if NULL, the tree's last quadrant is taken to be the end of the range.
  * `level`:[in] The level of the containing quadrant whose boundaries are tested: 0 if we want to test the boundaries of the whole tree.
  * `faces`:[in,out] An array of size 4 that is filled: faces[i] is true if the range touches that face.
  * `corners`:[in,out] An array of size 4 that is filled: corners[i] is true if the range touches that corner. **faces** or **corners** may be NULL.

### Returns

Returns an int32_t encoded with the same information in **faces** and **corners**: the first (least) four bits represent the four faces, the next four bits represent the four corners.

### Prototype

```c
int32_t p4est_find_range_boundaries (p4est_quadrant_t * lq, p4est_quadrant_t * uq, int level, int faces[], int corners[]);
```

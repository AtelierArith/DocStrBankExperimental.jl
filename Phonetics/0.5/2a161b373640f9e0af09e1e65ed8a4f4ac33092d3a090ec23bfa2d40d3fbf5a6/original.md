```
area(v::VowelSpace; unstandardize=true)
```

Returns the area of the passed in `VowelSpace`, `v`.

# Args

  * `v` The `VowelSpace` to calculate the area for
  * `unstandardize` (keyword) Flag to convert the semi-normalized F1 and F2 in `v` to Hz (or whatever units were passed in when `v` was created). Will cause the convex hull to be re-calculated to determine the vowel space area in this new space

# Returns

The area of the convex hull bounding the vowel space. Unit for area when F1 and F2 unstandardized back to Hz is Hz².

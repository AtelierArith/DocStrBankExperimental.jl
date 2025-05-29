```
rectanglePacking(h, w, rects, rot, alg)
```

Decides if perfect rectangle packing is possible and if so return it.

# Arguments

  * `h`: Height of rectangle to fill
  * `w`: Width of rectangle to fill
  * `rects`: Vector of rectangles to use for the packing; Encoded as Pair(height, width)
  * `rot`: If rectangles are allowed to be rotated by 90 degrees
  * `alg`: Which exhaustive algorithm to use

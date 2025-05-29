```
simple_ell(w1, h1; w2=h1, h2=w1)
```

Return an L-shaped polygon with its bottom left corner at the origin.

Note that the parameters describe the L as two overlapping rectangles. The result is identical if you switch "rectangle 1" and "rectangle 2". By default, the rectangles have the same "stroke width" and length.

```
_           |<------w2------->|
|           |▓▓▓▓|
|           |▓▓▓▓|
h1          |▓▓▓▓|
|           |<w1>|
|           |▓▓▓▓|
v           |▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓| h2
            ^ (x,y) = (0,0) at the lower-left corner of the L.
```

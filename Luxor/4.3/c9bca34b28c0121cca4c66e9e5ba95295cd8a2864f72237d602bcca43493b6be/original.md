```
brush(pt1, pt2, width=10;
    strokes=10,
    minwidth=0.01,
    maxwidth=0.03,
    twist = -1,
    lowhandle  = 0.3,
    highhandle = 0.7,
    randomopacity = true,
    tidystart = false,
    action = :fill,
    strokefunction = (nbpb) -> nbpb))
```

Draw a composite brush stroke made up of some randomized individual filled Bezier paths.

`strokefunction` allows a function to process a BezierPathSegment or do other things before it's drawn.

!!! note
    There is a lot of randomness in this function. Results are unpredictable.


```
Rectangle(width, height)
```

Constructs `Rectangle` objects by specifying the width and height rather than the lower-left and upper-right corners.

The rectangle will sit with the lower-left corner at the origin. With centered rectangles we would need to divide width and height by 2 to properly position. If we wanted an object of `Rectangle{Int}` type, this would not be possible if either `width` or `height` were odd numbers. This definition ensures type stability in the constructor.

`Rectangle` has the special importance of being the return type of `bounds`.

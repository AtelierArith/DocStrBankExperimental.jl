```
arrowhead(target[, action=:fill];
    shaftangle=0,
    headlength=10,
    headangle=pi/8)
```

Draw an arrow head. The arrowhead length will be the length of the side of the arrow's head, and the arrowhead angle is the angle between the sloping side of the arrowhead and the arrow's shaft.

This doesn't use the current linewidth setting (`setline()`), and defaults to 1, but you can specify another value.

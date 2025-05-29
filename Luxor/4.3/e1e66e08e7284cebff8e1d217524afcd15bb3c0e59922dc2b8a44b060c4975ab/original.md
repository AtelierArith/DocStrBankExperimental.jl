```
rect(cornerpoint, w, h; action = none, reversepath=false,
    vertices=false)
rect(cornerpoint, w, h, action; reversepath=false,
    vertices=false)
```

Create a rectangle with one corner at `cornerpoint` with width `w` and height `h`, and add it to the current path. Then apply `action`.

Use `vertices=true` to return an array of the four corner points: bottom left, top left, top right, bottom right.

`reversepath` reverses the direction of the path (and returns points in the order: bottom left, bottom right, top right, top left).

Returns the four corner vertices.

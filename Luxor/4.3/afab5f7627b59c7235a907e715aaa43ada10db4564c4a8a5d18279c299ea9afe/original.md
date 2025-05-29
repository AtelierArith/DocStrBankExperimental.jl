```
box(points::Array; action=:none,
    reversepath=reversepath,
    vertices=vertices)
box(points::Array; action=:none,
    reversepath=reversepath,
    vertices=vertices)
```

Create a box/rectangle using the first two points of an array of Points to defined opposite corners, and add it to the current path. Then apply `action`.

Use `vertices=true` to return an array of the four corner points: bottom left, top left, top right, bottom right rather than execute action.

```
box(cornerpoint1, cornerpoint2; action=:none, vertices=false, reversepath=false)
box(cornerpoint1, cornerpoint2, action; vertices=false, reversepath=false)
```

Create a box (rectangle) between two points and add it to the current path. Then apply `action`.

Use `vertices=true` to return an array of the four corner points: bottom left, top left, top right, bottom right rather than execute action.

`reversepath` reverses the direction of the path (and returns points in the order: bottom left, bottom right, top right, top left).

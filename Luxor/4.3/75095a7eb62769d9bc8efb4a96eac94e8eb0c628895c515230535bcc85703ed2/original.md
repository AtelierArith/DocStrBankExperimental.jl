```
box(pt::Point, width, height; action=:none, vertices=false)
box(pt::Point, width, height, action=:none; vertices=false)
```

Create a box/rectangle centered at point `pt` with width and height. Use `vertices=true` to return an array of the four corner points rather than apply the action.

`reversepath` reverses the direction of the path.

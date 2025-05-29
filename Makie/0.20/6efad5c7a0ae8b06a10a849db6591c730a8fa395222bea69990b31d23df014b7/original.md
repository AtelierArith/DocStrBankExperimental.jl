```
cam2d!(scene::SceneLike, kwargs...)
```

Creates a 2D camera for the given `scene`. The camera implements zooming by scrolling and translation using mouse drag. It also implements rectangle selections.

## Keyword Arguments

  * `zoomspeed = 0.1f0` sets the zoom speed.
  * `zoombutton = true` sets a button (combination) which needs to be pressed to enable zooming. By default no button needs to be pressed.
  * `panbutton = Mouse.right` sets the button used to translate the camera. This must include a mouse button.
  * `selectionbutton = (Keyboard.space, Mouse.left)` sets the button used for rectangle selection. This must include a mouse button.

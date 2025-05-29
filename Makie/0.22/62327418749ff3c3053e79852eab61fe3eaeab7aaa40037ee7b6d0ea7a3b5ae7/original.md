```
select_point(scene; kwargs...) -> point
```

Interactively select a point on a 2D `scene` by clicking the left mouse button, dragging and then un-clicking. Return an **observable** whose value corresponds to the selected point on the scene. In addition the function *plots* the point on the scene as the user clicks and moves the mouse around. When the button is not clicked any more, the plotted point disappears.

The value of the returned point is updated **only** when the user un-clicks.

The `kwargs...` are propagated into `scatter!` which plots the selected point.

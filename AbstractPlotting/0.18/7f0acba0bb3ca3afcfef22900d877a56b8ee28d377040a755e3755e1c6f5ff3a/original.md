```
select_rectangle(scene; kwargs...) -> rect
```

Interactively select a rectangle on a 2D `scene` by clicking the left mouse button, dragging and then un-clicking. The function returns an **observable** `rect` whose value corresponds to the selected rectangle on the scene. In addition the function *plots* the selected rectangle on the scene as the user clicks and moves the mouse around. When the button is not clicked any more, the plotted rectangle disappears.

The value of the returned observable is updated **only** when the user un-clicks (i.e. when the final value of the rectangle has been decided) and only if the rectangle has area > 0.

The `kwargs...` are propagated into `lines!` which plots the selected rectangle.

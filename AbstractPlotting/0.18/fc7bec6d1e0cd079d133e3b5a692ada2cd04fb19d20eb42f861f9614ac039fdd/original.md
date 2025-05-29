```
select_line(scene; kwargs...) -> line
```

Interactively select a line (typically an arrow) on a 2D `scene` by clicking the left mouse button, dragging and then un-clicking. Return an **observable** whose value corresponds to the selected line on the scene. In addition the function *plots* the line on the scene as the user clicks and moves the mouse around. When the button is not clicked any more, the plotted line disappears.

The value of the returned line is updated **only** when the user un-clicks and only if the selected line has non-zero length.

The `kwargs...` are propagated into `lines!` which plots the selected line.

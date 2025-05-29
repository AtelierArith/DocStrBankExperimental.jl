```
setclip(indicator::Int)
```

Set the clipping indicator.

**Parameters:**

`indicator` :     An indicator specifying whether clipping is on or off.

```
+----+---------------------------------------------------------------+
|   0|Clipping is off. Data outside of the window will be drawn.     |
+----+---------------------------------------------------------------+
|   1|Clipping is on. Data outside of the window will not be drawn.  |
+----+---------------------------------------------------------------+
```

`setclip` enables or disables clipping of the image drawn in the current window. Clipping is defined as the removal of those portions of the graph that lie outside of the defined viewport. If clipping is on, GR does not draw generated output primitives past the viewport boundaries. If clipping is off, primitives may exceed the viewport boundaries, and they will be drawn to the edge of the workstation window. By default, clipping is on.

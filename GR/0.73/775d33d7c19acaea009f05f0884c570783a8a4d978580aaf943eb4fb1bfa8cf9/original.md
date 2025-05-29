```
setfillstyle(index::Int)
```

Sets the fill style to be used for subsequent fill areas.

**Parameters:**

`index` :     The fill style index to be used

`setfillstyle` specifies an index when PATTERN fill or HATCH fill is requested by the `setfillintstyle` function. If the interior style is set to PATTERN, the fill style index points to a device-independent pattern table. If interior style is set to HATCH the fill style index indicates different hatch styles. If HOLLOW or SOLID is specified for the interior style, the fill style index is unused.

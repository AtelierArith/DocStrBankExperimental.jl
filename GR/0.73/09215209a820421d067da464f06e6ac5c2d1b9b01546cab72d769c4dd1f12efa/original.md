```
setlinewidth(width::Real)
```

Define the line width of subsequent polyline output primitives.

**Parameters:**

`width` :     The polyline line width scale factor

The line width is calculated as the nominal line width generated on the workstation multiplied by the line width scale factor. This value is mapped by the workstation to the nearest available line width. The default line width is 1.0, or 1 times the line width generated on the graphics device.

```
selntran(transform::Int)
```

`selntran` selects a predefined transformation from world coordinates to normalized device coordinates.

**Parameters:**

`transform` :     A normalization transformation number.

```
+------+----------------------------------------------------------------------------------------------------+
|     0|Selects the identity transformation in which both the window and viewport have the range of 0 to 1  |
+------+----------------------------------------------------------------------------------------------------+
|  >= 1|Selects a normalization transformation as defined by `setwindow` and `setviewport`                  |
+------+----------------------------------------------------------------------------------------------------+
```

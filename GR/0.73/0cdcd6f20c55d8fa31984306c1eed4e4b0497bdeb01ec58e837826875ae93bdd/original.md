```
setfillintstyle(style::Int)
```

Set the fill area interior style to be used for fill areas.

**Parameters:**

`style` :     The style of fill to be used

`setfillintstyle` defines the interior style  for subsequent fill area output primitives. The default interior style is HOLLOW.

```
+---------+---+--------------------------------------------------------------------------------+
|HOLLOW   |  0|No filling. Just draw the bounding polyline                                     |
+---------+---+--------------------------------------------------------------------------------+
|SOLID    |  1|Fill the interior of the polygon using the fill color index                     |
+---------+---+--------------------------------------------------------------------------------+
|PATTERN  |  2|Fill the interior of the polygon using the style index as a pattern index       |
+---------+---+--------------------------------------------------------------------------------+
|HATCH    |  3|Fill the interior of the polygon using the style index as a cross-hatched style |
+---------+---+--------------------------------------------------------------------------------+
```

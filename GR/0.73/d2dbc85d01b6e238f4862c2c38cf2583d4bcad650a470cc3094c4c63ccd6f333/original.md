```
setlinetype(style::Int)
```

Specify the line style for polylines.

**Parameters:**

`style` :     The polyline line style

The available line types are:

```
+---------------------------+----+---------------------------------------------------+
|LINETYPE_SOLID             |   1|Solid line                                         |
+---------------------------+----+---------------------------------------------------+
|LINETYPE_DASHED            |   2|Dashed line                                        |
+---------------------------+----+---------------------------------------------------+
|LINETYPE_DOTTED            |   3|Dotted line                                        |
+---------------------------+----+---------------------------------------------------+
|LINETYPE_DASHED_DOTTED     |   4|Dashed-dotted line                                 |
+---------------------------+----+---------------------------------------------------+
|LINETYPE_DASH_2_DOT        |  -1|Sequence of one dash followed by two dots          |
+---------------------------+----+---------------------------------------------------+
|LINETYPE_DASH_3_DOT        |  -2|Sequence of one dash followed by three dots        |
+---------------------------+----+---------------------------------------------------+
|LINETYPE_LONG_DASH         |  -3|Sequence of long dashes                            |
+---------------------------+----+---------------------------------------------------+
|LINETYPE_LONG_SHORT_DASH   |  -4|Sequence of a long dash followed by a short dash   |
+---------------------------+----+---------------------------------------------------+
|LINETYPE_SPACED_DASH       |  -5|Sequence of dashes double spaced                   |
+---------------------------+----+---------------------------------------------------+
|LINETYPE_SPACED_DOT        |  -6|Sequence of dots double spaced                     |
+---------------------------+----+---------------------------------------------------+
|LINETYPE_DOUBLE_DOT        |  -7|Sequence of pairs of dots                          |
+---------------------------+----+---------------------------------------------------+
|LINETYPE_TRIPLE_DOT        |  -8|Sequence of groups of three dots                   |
+---------------------------+----+---------------------------------------------------+
```

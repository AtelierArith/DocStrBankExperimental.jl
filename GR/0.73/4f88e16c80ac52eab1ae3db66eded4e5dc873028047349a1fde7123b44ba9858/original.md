```
settextalign(horizontal::Int, vertical::Int)
```

Set the current horizontal and vertical alignment for text.

**Parameters:**

`horizontal` :     Horizontal text alignment (see the table below) `vertical` :     Vertical text alignment (see the table below)

`settextalign` specifies how the characters in a text primitive will be aligned in horizontal and vertical space. The default text alignment indicates horizontal left alignment and vertical baseline alignment.

```
+-------------------------+---+----------------+
|TEXT_HALIGN_NORMAL       |  0|                |
+-------------------------+---+----------------+
|TEXT_HALIGN_LEFT         |  1|Left justify    |
+-------------------------+---+----------------+
|TEXT_HALIGN_CENTER       |  2|Center justify  |
+-------------------------+---+----------------+
|TEXT_HALIGN_RIGHT        |  3|Right justify   |
+-------------------------+---+----------------+

+-------------------------+---+------------------------------------------------+
|TEXT_VALIGN_NORMAL       |  0|                                                |
+-------------------------+---+------------------------------------------------+
|TEXT_VALIGN_TOP          |  1|Align with the top of the characters            |
+-------------------------+---+------------------------------------------------+
|TEXT_VALIGN_CAP          |  2|Aligned with the cap of the characters          |
+-------------------------+---+------------------------------------------------+
|TEXT_VALIGN_HALF         |  3|Aligned with the half line of the characters    |
+-------------------------+---+------------------------------------------------+
|TEXT_VALIGN_BASE         |  4|Aligned with the base line of the characters    |
+-------------------------+---+------------------------------------------------+
|TEXT_VALIGN_BOTTOM       |  5|Aligned with the bottom line of the characters  |
+-------------------------+---+------------------------------------------------+
```

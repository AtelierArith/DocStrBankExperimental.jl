```
settextfontprec(font::Int, precision::Int)
```

Specify the text font and precision for subsequent text output primitives.

**Parameters:**

`font` :     Text font (see tables below) `precision` :     Text precision (see table below)

The available text fonts are:

```
+--------------------------------------+-----+
|FONT_TIMES_ROMAN                      |  101|
+--------------------------------------+-----+
|FONT_TIMES_ITALIC                     |  102|
+--------------------------------------+-----+
|FONT_TIMES_BOLD                       |  103|
+--------------------------------------+-----+
|FONT_TIMES_BOLDITALIC                 |  104|
+--------------------------------------+-----+
|FONT_HELVETICA                        |  105|
+--------------------------------------+-----+
|FONT_HELVETICA_OBLIQUE                |  106|
+--------------------------------------+-----+
|FONT_HELVETICA_BOLD                   |  107|
+--------------------------------------+-----+
|FONT_HELVETICA_BOLDOBLIQUE            |  108|
+--------------------------------------+-----+
|FONT_COURIER                          |  109|
+--------------------------------------+-----+
|FONT_COURIER_OBLIQUE                  |  110|
+--------------------------------------+-----+
|FONT_COURIER_BOLD                     |  111|
+--------------------------------------+-----+
|FONT_COURIER_BOLDOBLIQUE              |  112|
+--------------------------------------+-----+
|FONT_SYMBOL                           |  113|
+--------------------------------------+-----+
|FONT_BOOKMAN_LIGHT                    |  114|
+--------------------------------------+-----+
|FONT_BOOKMAN_LIGHTITALIC              |  115|
+--------------------------------------+-----+
|FONT_BOOKMAN_DEMI                     |  116|
+--------------------------------------+-----+
|FONT_BOOKMAN_DEMIITALIC               |  117|
+--------------------------------------+-----+
|FONT_NEWCENTURYSCHLBK_ROMAN           |  118|
+--------------------------------------+-----+
|FONT_NEWCENTURYSCHLBK_ITALIC          |  119|
+--------------------------------------+-----+
|FONT_NEWCENTURYSCHLBK_BOLD            |  120|
+--------------------------------------+-----+
|FONT_NEWCENTURYSCHLBK_BOLDITALIC      |  121|
+--------------------------------------+-----+
|FONT_AVANTGARDE_BOOK                  |  122|
+--------------------------------------+-----+
|FONT_AVANTGARDE_BOOKOBLIQUE           |  123|
+--------------------------------------+-----+
|FONT_AVANTGARDE_DEMI                  |  124|
+--------------------------------------+-----+
|FONT_AVANTGARDE_DEMIOBLIQUE           |  125|
+--------------------------------------+-----+
|FONT_PALATINO_ROMAN                   |  126|
+--------------------------------------+-----+
|FONT_PALATINO_ITALIC                  |  127|
+--------------------------------------+-----+
|FONT_PALATINO_BOLD                    |  128|
+--------------------------------------+-----+
|FONT_PALATINO_BOLDITALIC              |  129|
+--------------------------------------+-----+
|FONT_ZAPFCHANCERY_MEDIUMITALIC        |  130|
+--------------------------------------+-----+
|FONT_ZAPFDINGBATS                     |  131|
+--------------------------------------+-----+
```

The available text precisions are:

```
+---------------------------+---+--------------------------------------+
|TEXT_PRECISION_STRING      |  0|String precision (higher quality)     |
+---------------------------+---+--------------------------------------+
|TEXT_PRECISION_CHAR        |  1|Character precision (medium quality)  |
+---------------------------+---+--------------------------------------+
|TEXT_PRECISION_STROKE      |  2|Stroke precision (lower quality)      |
+---------------------------+---+--------------------------------------+
```

The appearance of a font depends on the text precision value specified. STRING, CHARACTER or STROKE precision allows for a greater or lesser realization of the text primitives, for efficiency. STRING is the default precision for GR and produces the highest quality output.

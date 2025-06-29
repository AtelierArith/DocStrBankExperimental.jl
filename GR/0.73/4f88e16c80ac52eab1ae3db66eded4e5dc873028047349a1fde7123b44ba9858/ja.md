```
settextalign(horizontal::Int, vertical::Int)
```

テキストの現在の水平および垂直アラインメントを設定します。

**パラメータ:**

`horizontal` :     水平テキストアラインメント（下の表を参照） `vertical` :     垂直テキストアラインメント（下の表を参照）

`settextalign` は、テキストプリミティブ内の文字が水平および垂直空間でどのようにアラインされるかを指定します。デフォルトのテキストアラインメントは、水平左寄せおよび垂直ベースラインアラインメントを示します。

```
+-------------------------+---+----------------+
|TEXT_HALIGN_NORMAL       |  0|                |
+-------------------------+---+----------------+
|TEXT_HALIGN_LEFT         |  1|左寄せ         |
+-------------------------+---+----------------+
|TEXT_HALIGN_CENTER       |  2|中央寄せ       |
+-------------------------+---+----------------+
|TEXT_HALIGN_RIGHT        |  3|右寄せ         |
+-------------------------+---+----------------+

+-------------------------+---+------------------------------------------------+
|TEXT_VALIGN_NORMAL       |  0|                                                |
+-------------------------+---+------------------------------------------------+
|TEXT_VALIGN_TOP          |  1|文字の上部に揃える                              |
+-------------------------+---+------------------------------------------------+
|TEXT_VALIGN_CAP          |  2|文字のキャップに揃える                          |
+-------------------------+---+------------------------------------------------+
|TEXT_VALIGN_HALF         |  3|文字の半分のラインに揃える                      |
+-------------------------+---+------------------------------------------------+
|TEXT_VALIGN_BASE         |  4|文字のベースラインに揃える                      |
+-------------------------+---+------------------------------------------------+
|TEXT_VALIGN_BOTTOM       |  5|文字の下部ラインに揃える                        |
+-------------------------+---+------------------------------------------------+
```

```
function get_coordinates(obj, dimname) -> coordinates::Vector
```

`obj`に対して`dimname`に付随する座標（あれば）を取得します。

PALEOの規約では、可能な限り`coordinates`には以下が含まれます：

  * セルの中点、下端、上端のための3つの変数名（その順序で）。
  * セルの中点と境界変数のための2つの変数名（境界次元が最初の次元として）。

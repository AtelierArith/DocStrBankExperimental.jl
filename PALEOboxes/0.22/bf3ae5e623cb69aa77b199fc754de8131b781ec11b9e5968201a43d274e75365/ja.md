```
function get_coordinates(obj, dimname) -> coordinates::Vector
```

PALEOオブジェクト`obj`に対して`dimname`に付随する座標（あれば）を取得します。

PALEOの慣例では、可能な限り`coordinates`には以下が含まれます：

  * セルの中点、下端、上端の順に、3つの変数名。
  * セルの中点と境界変数（境界次元が最初の次元である）に対して、2つの変数名。

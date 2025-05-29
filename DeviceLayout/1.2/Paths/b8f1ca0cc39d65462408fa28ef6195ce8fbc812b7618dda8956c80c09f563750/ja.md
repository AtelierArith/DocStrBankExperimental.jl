```
turn!(p::Path, str::String, r::Coordinate, sty::Style=contstyle1(p))
```

パス `p` を文字列 `str` でコーディングされた方向に回転させます：

  * "l": 90° 回転 (左)
  * "r": -90° 回転 (右)
  * "lrlrllrrll": その順序で回転を行います

デフォルトでは、パスの最後の連続スタイルを使用します。

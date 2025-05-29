```
preserves_angles(f::Transformation)
```

`f`が角度を保持している（同じ大きさの固有値を持つ）場合は`true`を返し、それ以外の場合は`false`を返します。

浮動小数点の不正確さを考慮して近似等価を使用します。

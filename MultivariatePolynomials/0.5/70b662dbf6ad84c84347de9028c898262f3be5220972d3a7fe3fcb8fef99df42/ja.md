```
powers(t::AbstractTermLike)
```

`t`の単項式の冪に対するイテレータを返します。

### 例

`powers(3x^4*y)`を呼び出すと`((x, 4), (y, 1))`が返されるべきです。

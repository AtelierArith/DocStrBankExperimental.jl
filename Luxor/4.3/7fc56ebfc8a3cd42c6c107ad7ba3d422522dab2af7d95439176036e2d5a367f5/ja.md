```
isarcclockwise(c::Point, A::Point, B::Point)
```

`c`を中心とし、`A`から`B`に向かう弧が時計回りであれば`true`を返します。

`c`、`A`、`B`が共線の場合、半球状の弧は時計回りであるかどうかは不明です。

```
isrepresented(object::MLJType, objects)
```

`object`が反復可能な`objects`に代表があるかどうかをテストします。これは`object in objects`よりも弱い要件です。

ここでは、`m1`が`m2`を*表す*と言うとき、`is_same_except(m1, m2)`が`true`である場合を指します。

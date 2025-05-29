```
AttributeRecord <: Record
```

`Attribute`としてプロパティを格納する`Record`で、遅延評価のためのものです。

`getproperty`を呼び出すか、反復処理を行うと、アクセスされたプロパティが評価され、キャッシュされます。

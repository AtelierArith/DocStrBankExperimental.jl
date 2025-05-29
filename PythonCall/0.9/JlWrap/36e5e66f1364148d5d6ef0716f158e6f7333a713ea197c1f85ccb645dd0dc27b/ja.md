```
pyjltype(x)
```

`pyjl(x)`によってJuliaオブジェクト`x`がラップされる`juliacall.AnyValue`のサブタイプ。

`pyjltype(::T)`をオーバーロードして、あなたの型`T`のカスタム変換を定義します。

```
muscadeerror([[dbg,]msg])
```

`MuscadeException`をスローします。ここで、

  * `dbg`は、エラーメッセージと共に表示される「位置情報」を含む`NamedTuple`です。

（例えば：solver、step、iteration、element、quadrature point）

  * `msg`は、問題を説明する`String`です。

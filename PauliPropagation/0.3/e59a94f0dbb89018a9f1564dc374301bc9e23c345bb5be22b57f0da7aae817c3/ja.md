```
wrapcoefficients(pstr::PauliString, PathPropertiesType<:PathProperties)
```

`PauliString`の係数をカスタム`PathProperties`型にラップします。ライブラリでネイティブにサポートされていないものについては、`PathProperties`をサブタイプできます。係数からカスタム`PathProperties`型の1引数コンストラクタを定義する必要があります。

```
wrapcoefficients(psum::PauliSum, PathPropertiesType<:PathProperties)
```

`PauliSum`の係数をカスタム`PathProperties`型にラップします。ライブラリによってネイティブにサポートされていないものについては、`PathProperties`をサブタイプ化できます。係数からカスタム`PathProperties`型の1引数コンストラクタを定義する必要があります。

```
Sampleable{F<:VariateForm,S<:ValueSupport}
```

`Sampleable` はランダムな値を生成できる任意の型です。サンプルの次元を定義する `VariateForm` と、サンプリングされる可能性のある値のドメインを定義する `ValueSupport` によってパラメータ化されています。すべての `Sampleable` は `Base.rand` メソッドを実装しています。

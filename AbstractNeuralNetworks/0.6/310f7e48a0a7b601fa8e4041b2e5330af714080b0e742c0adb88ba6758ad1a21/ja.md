```
チェーン
```

チェーンは層のシーケンスです。

`Chain`は任意の数の層を渡すことで初期化できます。

```
Chain(layers...)
```

または、バックエンドとパラメータ型と共にニューラルネットワークアーキテクチャを指定することもできます。

```
Chain(::Architecture, ::NeuralNetworkBackend, ::Type; kwargs...)
Chain(::Architecture, ::Type; kwargs...)
```

バックエンドが省略された場合、デフォルトのバックエンド`CPU()`が選択されます。キーワード引数は各層の`initialparameters`メソッドに渡されます。

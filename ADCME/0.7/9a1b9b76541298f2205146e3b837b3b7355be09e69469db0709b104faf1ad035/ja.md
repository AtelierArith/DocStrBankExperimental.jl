```
ae_to_code(file::String, scope::String; activation::String = "tanh")
```

`file`内のフィードフォワードニューラルネットワークデータからコード文字列を返します。通常、次のようにしてコード文字列をJuliaセッションに即座に評価できます。

```julia
eval(Meta.parse(s))
```

`activation`が指定されていない場合、デフォルトは`tanh`です。

```
EmbedModelVia(model, F::Function; Domain::HyperCube=FullDomain(GetArgLength(F),Inf)) -> Union{Function,ModelMap}
```

モデル関数を `newmodel(x, θ) = oldmodel(x, F(θ))` を介して変換します。新しいモデルのための `Domain` は、`ModelMap` のためにオプションで指定できます。

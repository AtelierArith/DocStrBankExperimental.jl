```
(o::InferenceSession)(inputs [,output_names])
```

[`InferenceSession`](@ref)を入力のコレクションで実行します。ここで`inputs`は`NamedTuple`または`AbstractDict`のいずれかであることができます。オプションで`output_names`を渡すことができます。この場合、`output_names`に含まれる名前の出力のみが計算されます。

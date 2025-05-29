```
score = lecture_batched!(
    p::GenerativeFunction, p_args::Tuple,
    q::GenerativeFunction, get_q_args::Function)
```

pのトレーニングサンプルを表すトレースのバッチをシミュレートし、それを使用してqの学習可能なパラメータの勾配を更新します。

`lecture!`と同様ですが、qはバッチ処理され、階層アドレス空間i::Intの下でトレーニングサンプルiのためにランダムな選択を行う必要があります（例：i => :z）。get*q*argsはpのトレースのベクトルをqの引数タプルにマッピングします。

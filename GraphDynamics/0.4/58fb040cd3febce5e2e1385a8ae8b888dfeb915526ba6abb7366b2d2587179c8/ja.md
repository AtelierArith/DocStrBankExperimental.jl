```
initialize_input(::Subsystem{T})
```

与えられた `Subsystem` に対する入力の中立要素を生成します。これにより、

```julia
acc = initialize_input(sys)
combine(acc, another_input) == another_input
```

が成り立ちます。もし `combine` が単に入力を加算するだけであれば、`initialize_input` はゼロまたはゼロのコレクションであるべきです。

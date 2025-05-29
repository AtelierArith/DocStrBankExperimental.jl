```
Error(predicate; f="", exception=nothing))
```

イテレーション制御、例えば、`Error(m -> isnan(m.bias), f="バイアスオーバーフロー！")`。

もし `predicate(m)` が `true` の場合、`f` の値（または `f(IterationControl.expose(m))` が関数である場合）を `Error` レベルでログに記録し、現在の制御サイクルの終わりでイテレーションを停止します。ここで `m` はイテレートされているオブジェクトです。

`exception=...` を指定すると、制御サイクルの終わりを待たずに即座に例外をスローします。

[`Info`](@ref) や [`Warn`](@ref) も参照してください。

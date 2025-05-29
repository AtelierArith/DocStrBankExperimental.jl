```
Warn(predicate; f="")
```

イテレーション制御、例えば、`Warn(m -> length(m.cache) > 100, f="メモリ不足")`。

`predicate(m)` が `true` の場合、`f` の値を `Warn` にログします（または `f(IterationControl.expose(m))` もし `f` が関数の場合）。ここで `m` はイテレートされているオブジェクトです。

グローバルの冗長性レベルを十分に低く設定することで抑制できます。

[`Info`](@ref) や [`Error`](@ref) も参照してください。

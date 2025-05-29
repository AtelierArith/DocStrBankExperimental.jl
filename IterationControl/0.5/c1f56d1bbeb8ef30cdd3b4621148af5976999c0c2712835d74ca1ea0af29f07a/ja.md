```
Info(f=identity)
```

イテレーション制御、すなわち `Info(my_loss_function)` のように。

`f(m)` の値を `Info` にログします。ここで、`m` はイテレートされるオブジェクトです。もし `IterativeControl.expose(m)` がオーバーロードされている場合は、代わりに `f(expose(m))` をログします。

グローバルの冗長性レベルを十分に低く設定することで抑制できます。

他に [`Warn`](@ref)、[`Error`](@ref) も参照してください。

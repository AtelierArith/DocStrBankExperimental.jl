```
iterator(tracker::Tracker, x₁, t₁=1.0, t₀=0.0)
```

トラッカーを準備して、（状態を持つ）イテレーターとして使用できるようにします。特定のパスを調査したい場合に使用してください。各イテレーションでタプル `(x,t)` が返されます。

## 例

`Tracker` `tracker` があり、`x₁` を 1.0 から 0.25 まで追跡したいと仮定します：

```julia
for (x,t) in iterator(tracker, x₁, 1.0, 0.25)
    println("x at t=$t:")
    println(x)
end
```

これは状態を持つイテレーターであることに注意してください。トラッカーの状態を調査することもできます。たとえば、トラッカーが成功したかどうか（何らかの問題で早期に終了しなかったか）を確認するには、次のようにします。

```julia
println("Success: ", is_success(status(tracker)))
```

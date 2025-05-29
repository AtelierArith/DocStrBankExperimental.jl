```
CyclicBehavior(action)
```

繰り返し実行される循環的な動作を作成します。`action(a::Agent, b::Behavior)` 関数は、動作が実行されるときに呼び出されます。動作の `onstart` および `onend` フィールドには、動作が初期化されるときと終了するときに呼び出される関数を設定できます。両方の関数は、`action` と同様のパラメータで呼び出されます。

循環的な動作の実行は、`block(b)`、`restart(b)`、および `stop(b)` を使用して制御できます。

# 例:

```julia
using Fjage

@agent struct MyAgent end

function Fjage.startup(a::MyAgent)
  add(a, CyclicBehavior() do a, b
    @info "CyclicBehavior running..."
  end)
end
```

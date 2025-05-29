```
OneShotBehavior(action)
```

一度だけ実行されるワンショットビヘイビアを作成します。`action(a::Agent, b::Behavior)` 関数は、ビヘイビアが実行されるときに呼び出されます。ビヘイビアの `onstart` および `onend` フィールドには、ビヘイビアが初期化されるときと終了するときに呼び出される関数を設定できます。両方の関数は、`action` と同様のパラメータで呼び出されます。

# 例:

```julia
using Fjage

@agent struct MyAgent end

function Fjage.startup(a::MyAgent)
  add(a, OneShotBehavior() do a, b
    @info "OneShotBehavior just ran"
  end)
end
```

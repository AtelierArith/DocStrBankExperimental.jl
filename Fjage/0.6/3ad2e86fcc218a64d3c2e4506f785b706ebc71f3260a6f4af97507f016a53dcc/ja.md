```
WakerBehavior(action, millis)
```

`millis`ミリ秒後に正確に1回実行される動作を作成します。動作が実行されるときに`action(a::Agent, b::Behavior)`関数が呼び出されます。動作が初期化されるときと終了するときに呼び出される関数を設定できる`onstart`および`onend`フィールドがあります。両方の関数は`action`と同様のパラメータで呼び出されます。

# 例:

```julia
using Fjage

@agent struct MyAgent end

function Fjage.startup(a::MyAgent)
  add(a, WakerBehavior(5000) do a, b
    @info "5秒後に目が覚めました！"
  end)
end
```

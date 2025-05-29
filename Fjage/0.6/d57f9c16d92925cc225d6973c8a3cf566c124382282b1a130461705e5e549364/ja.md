```
TickerBehavior(action, millis)
```

`millis`ミリ秒ごとに定期的に実行されるビヘイビアを作成します。ビヘイビアが実行されるときに呼び出される`action(a::Agent, b::Behavior)`関数があります。ビヘイビアの`onstart`および`onend`フィールドには、ビヘイビアが初期化されるときと終了するときに呼び出される関数を設定できます。両方の関数は`action`と同様のパラメータで呼び出されます。

# 例:

```julia
using Fjage

@agent struct MyAgent end

function Fjage.startup(a::MyAgent)
  add(a, TickerBehavior(5000) do a, b
    @info "Tick!"
  end)
end
```

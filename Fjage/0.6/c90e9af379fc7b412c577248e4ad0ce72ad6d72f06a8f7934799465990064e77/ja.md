```
PoissonBehavior(action, millis)
```

平均して `millis` ミリ秒ごとにランダムに実行される振る舞いを作成します。`action(a::Agent, b::Behavior)` 関数は振る舞いが実行されるときに呼び出されます。振る舞いの `onstart` および `onend` フィールドには、振る舞いが初期化されるときと終了するときに呼び出される関数を設定できます。両方の関数は `action` と同様のパラメータで呼び出されます。

# 例:

```julia
using Fjage

@agent struct MyAgent end

function Fjage.startup(a::MyAgent)
  add(a, PoissonBehavior(5000) do a, b
    @info "PoissonBehavior ran!"
  end)
end
```

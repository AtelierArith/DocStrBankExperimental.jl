```
BackoffBehavior(action, millis)
```

`millis` ミリ秒後に実行される動作を作成します。動作が実行されるときに `action(a::Agent, b::Behavior)` 関数が呼び出されます。動作は `backoff(b, t)` を呼び出すことで `t` ミリ秒後に再実行するようにスケジュールできます。

動作の `onstart` および `onend` フィールドには、動作が初期化されるときと終了するときに呼び出される関数を設定できます。両方の関数は `action` と同様のパラメータで呼び出されます。

`BackoffBehavior` コンストラクタは、`backoff()` を使用して頻繁に再スケジュールされることを意図した `WakerBehavior` の単なる構文糖です。

# 例:

```julia
using Fjage

@agent struct MyAgent end

function Fjage.startup(a::MyAgent)
  # 5秒後に初めて実行され、その後は
  # 2秒ごとに実行される動作
  add(a, BackoffBehavior(5000) do a, b
    @info "Backoff!"
    backoff(b, 2000)
  end)
end
```

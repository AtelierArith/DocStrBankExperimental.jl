```
MessageBehavior(action, millis)
MessageBehavior(action, filt, millis)
```

メッセージが到着するたびに実行される動作を作成します。メッセージが到着すると、`action(a::Agent, b::Behavior, msg)` 関数が呼び出されます。動作の `onstart` および `onend` フィールドには、動作が初期化されるときと終了するときに呼び出される関数を設定できます。両方の関数は、`action` と同様のパラメータで呼び出されます。

フィルター `filt` が指定されている場合、フィルターに一致するメッセージのみがこの動作をトリガーします。フィルターはメッセージクラスまたはメッセージを引数として受け取り、受け入れる場合は `true`、拒否する場合は `false` を返す関数である可能性があります。

メッセージに一致する複数の `MessageBehavior` がアクティブな場合、そのうちの1つだけがメッセージを受け取ります。受け取る動作は、その `priority` フィールドに基づいて選択されます。フィルター付きのメッセージは、フィルターなしのメッセージよりも高いデフォルトの優先度が与えられます。

エージェントのデフォルト `init()` は、自動的に `MessageBehavior` を追加して、`processrequest()` または `processmessage()` メソッドにメッセージをディスパッチします。したがって、エージェントはそれらの関数のためのメソッドを提供することでメッセージを処理できます。ただし、エージェントが独自の `init()` メソッドを提供する場合、受信メッセージを処理するために `MessageBehavior` を使用する必要があります。

# 例:

```julia
using Fjage

const MySpecialNtf = MessageClass(@__MODULE__, "MySpecialNtf")

@agent struct MyAgent end

function Fjage.init(a::MyAgent)
  add(a, MessageBehavior(MySpecialNtf) do a, b, msg
    @info "特別なメッセージを受け取りました: $msg"
  end)
  add(a, MessageBehavior() do a, b, msg
    @info "あまり特別ではないメッセージを受け取りました: $msg"
  end)
end
```

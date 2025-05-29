```
subscribe_event(role::Role, event_type::Any, event_handler::Any, condition::Function)
```

特定のタイプのイベントにサブスクライブします。

イベントのタイプは、`condition` 関数（`src` と `event` を受け取る）と `event_type` によって決まります。

# 例

```julia
struct MyEvent end
function custom_handler(role::Role, src::Role, event::Any, event_type::Any)
    # あなたの処理を行う
end
subscribe_event(my_role, MyEvent, custom_handler, (src, event) -> aid(src) == "agent0")
```

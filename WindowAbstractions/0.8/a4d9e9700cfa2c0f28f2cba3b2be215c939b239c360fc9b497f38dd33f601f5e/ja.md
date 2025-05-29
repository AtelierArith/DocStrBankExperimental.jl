```
save_history(wm::WM, queue::EventQueue{WM}) -> Vector{<:Event}
```

イベントキュー内に保存されたアクションを、後で[`replay_history`](@ref)で再生するために保存します。

イベントキューは`record_history = true`で作成されている必要があります。

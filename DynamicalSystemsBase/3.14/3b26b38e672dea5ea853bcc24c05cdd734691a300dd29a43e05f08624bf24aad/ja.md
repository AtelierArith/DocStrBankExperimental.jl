```
set_state!(ds::DynamicalSystem, u::AbstractArray{<:Real})
```

`ds`の状態を`u`に設定します。`u`は`ds`の次元と一致する必要があります。また、変更が使用される統合プロトコルに通知されることを確認してください。

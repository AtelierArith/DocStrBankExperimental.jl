```
EveryStepCallback(affect, finalize)
```

シミュレーション状態に対して、すべての [`prepropagate!`](@ref) フックで関数 `affect` を呼び出す汎用コールバックです。シミュレーションが正常に終了した際に `finalize` を呼び出します（詳細は [`finalize!`](@ref）を参照）。

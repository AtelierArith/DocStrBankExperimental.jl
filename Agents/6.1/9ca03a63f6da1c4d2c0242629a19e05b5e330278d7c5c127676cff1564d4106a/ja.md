```
walk!(agent, direction::NTuple, model::ABM{<:AbstractGridSpace}; ifempty = true)
walk!(agent, direction::SVector, model::ABM{<:ContinuousSpace})
```

与えられた`direction`に従ってエージェントを移動させ、周期的境界条件を尊重します。非周期的空間では、エージェントは境界値を超えずに移動します。`AbstractGridSpace`と`ContinuousSpace`の両方で利用可能です。

`direction`の型は空間の位置と同じでなければなりません。`AbstractGridSpace`は`Int`タプルを要求し、`ContinuousSpace`は`Float64`静的ベクトルを要求し、各方向の移動距離を示します。`direction = (2, -3)`は`AbstractGridSpace`での有効な方向の例で、エージェントを右に2位置、下に3位置移動させます。エージェントの速度は`ContinuousSpace`でのこの操作では無視されます。

## キーワード

  * `ifempty`は、ターゲット位置が占有されていないことを確認し、それが真である場合にのみ移動します。`AbstractGridSpace`でのみ利用可能です。

[Battle Royale](     https://juliadynamics.github.io/AgentsExampleZoo.jl/dev/examples/battle/)での使用例。

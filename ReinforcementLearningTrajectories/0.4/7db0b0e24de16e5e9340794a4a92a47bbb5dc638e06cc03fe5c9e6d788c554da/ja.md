```
Trajectory(container, sampler, controller)
```

`container`は経験を保存するために使用されます。一般的なものには[`Traces`](@ref)や[`Episodes`](@ref)があります。`sampler`は`container`から経験のバッチをサンプリングするために使用されます。`controller`はバッチをサンプリングする時期を制御します。

サポートされているメソッドは次のとおりです：

  * `push!(t::Trajectory, experience)`、1つの経験を軌道に追加します。
  * `append!(t::Trajectory, batch)`、経験のバッチを軌道に追加します。
  * `take!(t::Trajectory)`、軌道から経験のバッチを取得します。`nothing`が返される場合があり、これはまだサンプリングの準備ができていないことを示します。

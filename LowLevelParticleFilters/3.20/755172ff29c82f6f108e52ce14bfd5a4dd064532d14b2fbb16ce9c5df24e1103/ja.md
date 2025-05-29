```
forward_trajectory(imm::IMM, u, y, p = parameters(imm); interact = true)
```

バッチフィルタリングを[`IMM`](@ref)フィルタを使用して行う際、次のことができます。

  * フィルタの`interact`パラメータをオーバーライドする
  * 軌道に沿ったモード確率に`sol.extra`フィールドとしてアクセスする。これはサイズが`(n_modes, T)`の行列で、`T`は軌道の長さ（`u`と`y`の長さ）です。

返される解オブジェクトは[`KalmanFilteringSolution`](@ref)型で、次のフィールドを持っています：

```
ssrand(T::Type, ny::Int, nu::Int, nstates::Int; proper=false, stable=true, Ts=nothing)
```

`ny` 出力、`nu` 入力、`nstates` 状態を持つランダムな `StateSpace` モデルを返します。その行列要素は正規分布に従います。

システムが `proper` であるか `stable` であるかを指定することができます。

サンプル時間 `Ts` を指定すると、離散時間システムを取得できます。

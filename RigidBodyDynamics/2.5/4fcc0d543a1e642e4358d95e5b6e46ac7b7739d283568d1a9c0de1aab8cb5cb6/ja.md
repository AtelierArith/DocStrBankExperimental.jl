```julia
point_jacobian!(out, state, path, point)

```

ジョイントパスのターゲットに固定された点の速度を、ジョイントの速度ベクトル $v$ からマッピングするヤコビアンを計算します（パス内の最後のジョイントに続くボディ）を、ジョイントパスのソースに対して（パス内の最初のジョイントに先行するボディ）。

必要に応じて、`state` を使用して `Mechanism` のルートフレームから `out` が表現されているフレームへの変換を計算します。

このメソッドは、動的メモリ割り当てを行わずにインプレースで計算を行います。

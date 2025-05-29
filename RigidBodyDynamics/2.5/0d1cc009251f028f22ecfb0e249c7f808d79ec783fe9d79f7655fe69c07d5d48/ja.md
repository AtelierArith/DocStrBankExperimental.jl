```julia
Mechanism(root_body; gravity)

```

ルートボディのみを含む新しい `Mechanism` を作成し、他のボディをジョイントで接続できます。

`gravity` キーワード引数を使用して重力加速度を設定できます（`Mechanism` のルートフレームで表現された3ベクトル）。デフォルト: `[0.0, 0.0, -9.81]`。

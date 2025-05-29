```
sys = ss(A, B, C, D)      # 連続
sys = ss(A, B, C, D, Ts)  # 離散
sys = ss(P::TransferFunction; balance=true, minimal=false) # TransferFunctionをStateSpaceに変換

行列要素型 `T` を持つ状態空間モデル `sys::StateSpace{TE, T}` を作成します。TE は `Continuous` または `<:Discrete` です。

`Ts` が省略されると、これは連続時間モデルです。それ以外の場合、これはサンプリング周期 `Ts` を持つ離散時間モデルです。

`D` は `0` として指定することができ、その場合は適切なサイズのゼロ行列が自動的に構築されます。 `sys = ss(D [, Ts])` は静的ゲイン行列 `D` を指定します。

転送関数 `P` を状態空間モデルに変換する際、ユーザーは状態空間モデルをバランスさせるかどうか（デフォルトはtrue）および/または最小実現を返すかどうか（デフォルトはfalse）を選択できます。この変換には他のキーワード引数オプションがあり、詳細については `?ControlSystemsBase.MatrixPencils.rm2ls` を参照してください。

状態変数、入力、および出力に名前を関連付けるには、[`named_ss`](https://juliacontrol.github.io/RobustAndOptimalControl.jl/dev/#Named-systems) を参照してください。
```

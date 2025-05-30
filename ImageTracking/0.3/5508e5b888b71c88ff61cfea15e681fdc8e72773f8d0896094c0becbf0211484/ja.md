```
flow, indicator  = optical_flow(source, target, points, LucasKanade(Args...))
flow, indicator  = optical_flow(source, target, points, displacement, LucasKanade(Args...))
```

`source` から `target` 画像への光学フローを指定された `points` に対して `LucasKanade` アルゴリズムを使用して返します。

# 詳細

`source` と `target` 画像は `Gray` タイプでなければなりません。

`points` 引数は `Array{SVector{2, Float64}, 2}` 型で、光学フローを計算するための `source` 画像内のキーポイントのセットを表します。`point` の座標は画像内のピクセルの `(row, column)` を表します。`displacement` 引数を使用すると、光学フローの初期推定を指定できます。

この関数は、`points` の長さに一致する `Array{SVector{2, Float64}, 2}` 型の `flow` を返し、`source` 画像内の点を `target` 画像にマッピングするために必要な変位を表します。

`indicator` はブール値のベクトル（`points` 内の各点に対して1つ）で、特定の点が正常に追跡されたかどうかを示します。

`flow` を使用して `target` 画像内の対応する点をインデックスするには、まずそれを最も近い整数に丸め、`target` 画像の次元の範囲内に収まるかどうかを確認する必要があります。

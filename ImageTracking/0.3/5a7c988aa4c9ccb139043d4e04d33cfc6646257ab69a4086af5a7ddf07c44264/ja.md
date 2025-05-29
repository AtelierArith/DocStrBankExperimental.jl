```
flow = optical_flow(source, target, Farneback(Args...))
flow = optical_flow(source, target, displacement, Farneback(Args...))
```

`source` から `target` 画像への密な光学フローを `Farneback` アルゴリズムを使用して返します。

# 詳細

`source` と `target` 画像は `Gray` タイプでなければなりません。

`displacement` 引数は光学フローの初期推定を指定することを可能にし、型は `Array{SVector{2, Float64}, 2}` でなければなりません。`displacement` の要素は、`source` 画像の各ピクセルの `(row, column)` を `target` 画像にマッピングするために必要なフローを表す必要があります。

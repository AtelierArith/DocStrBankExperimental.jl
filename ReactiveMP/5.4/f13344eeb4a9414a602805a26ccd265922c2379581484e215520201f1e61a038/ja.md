```
ForwardDiffGrad(chunk_size::Int)
```

CVI手続きのための自動微分バックエンド。`ForwardDiff`ライブラリを使用して勾配/導関数を計算します。`chunk_size`が指定されていない場合は、`ForwardDiff`からのヒューリスティックを使用しますが、これは型不安定です。

!!! note
    `ForwardDiff.jl`は現在のJulia環境に追加する必要があります。


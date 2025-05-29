```
Aeration(; name, k_La=240, S_O_max=8)
```

酸素移動係数 k_L*a と酸素飽和濃度を使用して、単純な曝気プロセスを定義するコンポーネントです。

# パラメータ:

  * `k_La` 初期酸素移動係数 (デフォルト 240 1/d)
  * `S_O_max` 酸素の飽和濃度 (デフォルト 8 g/m^3)

# 状態:

  * `S_O` 酸素

# コネクタ

  * `state` 接続する反応器の状態 (溶存酸素のみ)
  * `rate` 計算された速度 (溶存酸素のみ)
  * `k_La` 酸素移動係数。 [`ModelingToolkitStandardLibrary.Blocks.RealInput`](@extref) であり、`ModelingToolkitStandardLibrary` のシステムと共に使用するためのもので、例えばコントローラーを提供します。

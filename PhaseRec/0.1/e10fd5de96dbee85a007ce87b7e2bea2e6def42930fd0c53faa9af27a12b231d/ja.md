```
phaserec(s2ft, size; radius = 0.6, maxstep = 300, ϵ = 10^-5[, noise])
```

二点相関関数から画像を再構成します。`s2ft`は周波数領域における非正規化二点相関関数で、`size`は元の画像の次元です。オプションのパラメータ`radius`はノイズフィルタリングを制御します。`maxsteps`は最大反復回数です。小さい`ϵ`は通常、より良い結果を生み出しますが、デフォルト値はすべてのケースで問題ないはずです。`noise`は初期近似を含むブール値のオプション配列です。

# 参考文献

1. A. Cherkasov, A. Ananev, Adaptive phase-retrieval stochastic reconstruction with correlation functions: Three-dimensional images from two-dimensional cuts, Phys. Rev. E, 104, 3, 2021

関連情報: [`two_point`](@ref).

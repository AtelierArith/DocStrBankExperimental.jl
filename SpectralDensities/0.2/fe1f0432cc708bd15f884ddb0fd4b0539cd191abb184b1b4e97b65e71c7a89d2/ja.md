```
memory_kernel(J::AbstractSD, τ)
```

スペクトル密度 `J` のメモリーカーネルを、与えられた時間遅延 `τ` で計算します。すなわち、

$$
\mathcal{K}(\tau) = 2\Theta(\tau)\int_0^\infty J(\omega)\sin(\omega)\mathrm{d}\omega,
$$

ここで、$\Theta$ はヘヴィサイドのθ関数です。

# 引数

  * `J::AbstractSD`: スペクトル密度。
  * `τ`: メモリーカーネルが評価される時間遅延。

# 戻り値

  * 与えられた時間遅延 `τ` におけるスペクトル密度 `J` のメモリーカーネル。

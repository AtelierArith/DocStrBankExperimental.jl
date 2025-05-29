```
acn(x, snr_dB, fs, color = :pink; band_freq = Float64[], rst = true)
```

信号 `x` に与えられた SNR で複雑なカラーノイズ (ACN) を追加します

**入力**

  * `x`: 信号
  * `snr_dB`: 信号対雑音比 [dB]
  * `fs`: サンプリング周波数 [Hz]
  * `color`: ノイズの色

      * `:white`
      * `:pink` (デフォルト)
      * `:blue`
      * `:brown`
      * `:purple`
  * `band_freq`: カラーノイズに適用されるバンドパスフィルタを定義するために使用される周波数
  * `rst`: 擬似乱数生成器をリセットする

**出力**

  * `y`: ノイズのある信号

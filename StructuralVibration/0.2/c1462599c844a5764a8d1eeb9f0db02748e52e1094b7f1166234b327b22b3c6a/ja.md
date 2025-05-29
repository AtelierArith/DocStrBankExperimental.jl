```
acn(x, snr_dB, freq, color = :pink; rst = true)
```

信号 `x` に与えられた SNR で複雑なランダムカラーノイズ (ACN) を追加します。

**入力**

  * `x::VecOrMat{Real}`: 信号
  * `snr_dB`: 信号対雑音比 [dB]
  * `freq::AbstractVector`: 興味のある周波数範囲
  * `color`: ノイズの色

      * `:white`
      * `:pink` (デフォルト)
      * `:blue`
      * `:brown`
      * `:purple`
  * `rst::Bool`: ランダム数生成器をリセットするかどうか

**出力**

  * `y`: ノイズのある信号

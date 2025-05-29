```
spectrum_correlation_fft(tlist, corr; inverse=false)
```

2時相関関数に対応するパワースペクトルを高速フーリエ変換（FFT）を使用して計算します。

# パラメータ

  * `tlist::AbstractVector`: 2時相関関数が与えられる時刻のリスト。
  * `corr::AbstractVector`: `tlist`の指定された時点に対応する2時相関のリスト。
  * `inverse::Bool`: 逆フーリエ変換を使用するかどうか。デフォルトは`false`。

# 戻り値

  * `ωlist`: 角周波数のリスト $\omega$。
  * `Slist`: `ωlist`の角周波数に対応するパワースペクトルのリスト。

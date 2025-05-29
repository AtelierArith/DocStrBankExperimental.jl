```
rfft(f::AbstractField, t::AbstractRange)
```

実数値信号の場合、均一な時間グリッド`t`でサンプリングされたフィールド`f`の[`field_amplitude`](@ref)のRFFTを計算します。

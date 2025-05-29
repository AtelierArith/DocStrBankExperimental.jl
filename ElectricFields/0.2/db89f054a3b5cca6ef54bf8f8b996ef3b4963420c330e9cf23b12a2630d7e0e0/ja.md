```
nfft(f::AbstractField, t::AbstractRange)
```

フィールド `f` の [`field_amplitude`](@ref) の対称的に正規化されたFFTを、均一な時間グリッド `t` でサンプリングして計算します。

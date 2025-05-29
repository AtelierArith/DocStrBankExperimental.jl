```
mt_spectrogram(signal::AbstractVector, mt_config::MTConfig,
               n_overlap::Int=mt_config.n_samples >> 1) -> Spectrogram
```

[`MTConfig`](@ref) オブジェクトを使用してウィンドウサイズを選択し、マルチテーパーのスペクトログラムを計算します。すべてのワークスペース変数は [`MTConfig`](@ref) オブジェクトに含まれており、このオブジェクトはスペクトログラム計算の間に再利用できるため、出力のみを割り当てる必要があります。

`Spectrogram` を返します。

[`mt_spectrogram!`](@ref) も参照してください。

## 例

```julia
signal1 = sin.(10_000) .+ randn(10_000)
mt_config = MTConfig{Float64}(1000) # 1000 samples per window
spec1 = mt_spectrogram(signal1, mt_config, 500)
signal2 = cos.(2_000) .+ randn(2_000)
spec2 = mt_spectrogram(signal2, mt_config, 250) # 同じ `mt_config`、異なる信号、異なるオーバーラップ
```

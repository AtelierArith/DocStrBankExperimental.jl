```
MTConfig{T}(n_samples; fs=1,
        nfft = nextpow(2, n_samples),
        window = nothing,
        nw = 4,
        ntapers = 2 * nw - 1,
        taper_weights = fill(1/ntapers, ntapers),
        onesided::Bool=T<:Real,
        fft_flags = FFTW.MEASURE)
```

マルチテーパー計算で使用される構成状態と一時変数を保持する構成オブジェクトを作成します。例えば、[`mt_pgram!`](@ref)、[`mt_spectrogram`](@ref)、[`MTSpectrogramConfig`](@ref)、[`MTCrossSpectraConfig`](@ref)、および[`MTCoherenceConfig`](@ref)などです。

`MTConfig`は、入力引数が変更されない限り、計算間で再利用できます。

  * `n_samples`: この構成を使用してマルチテーパー周期グラムを計算する際に使用されるサンプル数。一時バッファを事前に割り当てるために使用されます。
  * `fs`: 入力信号のサンプル数/秒
  * `nfft`: FFTへの入力ベクトルの長さ; `nfft > n_samples`の場合、入力信号は長さ`nfft`になるまでゼロパディングされます。
  * `window`: テーパーに使用するウィンドウ関数。デフォルトの`nothing`のままにすると、`window`は`dpss(n_samples, nw, ntapers)`に設定されます。
  * `ntapers`: 使用するテーパーの数。
  * `taper_weights = fill(1/ntapers, ntapers)`: 各テーパーの寄与をどのように重み付けするか。デフォルト設定は単に平均を取ることです。
  * `onesided`: 実信号データを使用して「片側」FFTを計算するかどうか。これはフーリエ空間で共役対称性をもたらします。
  * `fft_flags`: FFTプランの生成方法を制御するフラグ。

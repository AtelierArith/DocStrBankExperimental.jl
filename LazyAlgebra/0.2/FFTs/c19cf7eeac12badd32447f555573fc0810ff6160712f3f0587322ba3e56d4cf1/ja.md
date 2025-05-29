```julia
FFTOperator(A) -> F
```

は、`A`に似た配列の高速フーリエ変換を計算するのに適したFFTオペレーターを生成します。このオペレーターは、変換する配列の要素の実数/複素数浮動小数点型とその次元を指定することもできます：

```julia
FFTOperator(T, dims) -> F
```

ここで、`T`は`Float64`、`Float32`（実数-複素数FFT用）、`Complex{Float64}`、`Complex{Float32}`（複素数-複素数FFT用）のいずれかであり、`dims`は変換する配列の次元を指定します（`Direct`または`InverseAdjoint`操作によって）。

このようなオペレーターを作成する利点は、FFTの高速計算に必要なリソースをキャッシュするため、`fft`、`rfft`、`ifft`などを呼び出すよりも*はるかに*高速である可能性があることです。これは特に小さな配列に当てはまります。キーワード`flags`と`timelimit`を使用して、FFTプランを作成するための計画オプションと時間制限を指定できます（http://www.fftw.org/doc/Planner-Flags.htmlを参照）。デフォルトは`flags=FFTW.MEASURE`で、時間制限はありません。

`FFTOperator`のインスタンスは、他のマッピングと同様に使用できる線形マッピングです：

```julia
F*x     # xのFFTを生成
F'*x    # xに適用された随伴FFT、すなわちxの逆FFTを生成
F\x     # xの逆FFTを生成
```

参照： [`fft`](@ref)、[`plan_fft`](@ref)、[`bfft`](@ref)、           [`plan_bfft`](@ref)、[`rfft`](@ref)、[`plan_rfft`](@ref)、           [`brfft`](@ref)、[`plan_brfft`](@ref)。

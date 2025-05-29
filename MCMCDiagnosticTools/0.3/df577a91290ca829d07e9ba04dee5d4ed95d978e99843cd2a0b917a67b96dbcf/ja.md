```
FFTAutocovMethod <: AbstractAutocovMethod
```

`FFTAutocovMethod`は、MCMCチェーンの平均自己共分散を推定するための標準アルゴリズムを使用します。

アルゴリズムは[`AutocovMethod`](@ref)のものと同じですが、このメソッドは自己相関を推定するために高速フーリエ変換（FFT）を使用します。

!!! info
    このメソッドを使用するには、[AbstractFFTs.jl](https://github.com/JuliaMath/AbstractFFTs.jl)インターフェースを実装したパッケージ（[FFTW.jl](https://github.com/JuliaMath/FFTW.jl)や[FastTransforms.jl](https://github.com/JuliaApproximation/FastTransforms.jl)など）をロードする必要があります。


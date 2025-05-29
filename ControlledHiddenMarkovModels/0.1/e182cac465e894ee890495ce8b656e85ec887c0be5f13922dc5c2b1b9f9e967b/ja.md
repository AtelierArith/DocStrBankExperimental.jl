```
emission_distribution(hmm::AbstractControlledHMM, s, θ)
```

状態`s`における`hmm`の放出分布を、放出パラメータ`θ`を用いて計算します。`θ`は[`emission_parameters(hmm, control, par)`](@ref)を使用して計算されたことに注意してください。

返されるオブジェクトはサンプリング可能で、[DensityInterface.jl](https://github.com/JuliaMath/DensityInterface.jl)を実装している必要があります。

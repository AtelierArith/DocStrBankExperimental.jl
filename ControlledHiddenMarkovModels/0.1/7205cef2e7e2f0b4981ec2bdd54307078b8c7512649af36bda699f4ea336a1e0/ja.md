```
emission_distribution(hmm::AbstractHMM, s, par)
```

状態`s`における`hmm`の発生分布をパラメータ`par`を用いて計算します。

返されるオブジェクトはサンプリング可能であり、[DensityInterface.jl](https://github.com/JuliaMath/DensityInterface.jl)を実装している必要があります。

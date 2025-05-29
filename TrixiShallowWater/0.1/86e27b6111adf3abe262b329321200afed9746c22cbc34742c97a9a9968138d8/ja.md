```
flux_hll_chen_noelle = FluxHLL(min_max_speed_chen_noelle)
```

[`Trixi.FluxHLL`](@extref)のインスタンスで、浅水方程式に特化しており、[`min_max_speed_chen_noelle`](@ref)からの波速推定を使用します。このHLLフラックスは、「乾燥」要素からの数値的質量フラックスがゼロであることが保証されており、水の高さの正の値を維持し、エントロピー不等式を満たします。

詳細については、以下の参考文献のセクション2.4を参照してください。

  * Guoxian Chen and Sebastian Noelle (2017) A new hydrostatic reconstruction scheme based on subcell reconstructions [DOI: 10.1137/15M1053074](https://doi.org/10.1137/15M1053074)

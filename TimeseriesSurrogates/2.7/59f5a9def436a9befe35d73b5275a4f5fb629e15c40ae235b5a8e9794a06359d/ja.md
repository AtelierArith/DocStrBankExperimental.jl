```
PartialRandomizationAAFT(α = 0.5)
```

`PartialRandomizationAAFF` サロゲートは [`PartialRandomization`](@ref) サロゲート[^Ortega1998] に似ていますが、サロゲートが元の時系列と同じ値を持つように再スケーリングステップを追加します（[`AAFT`](@ref) サロゲートのために行われる再スケーリングに類似しています）。部分的なランダム化サロゲートは、パッケージの著者の知識の限りでは、科学文献に発表されていません。

[^Ortega1998]: Ortega, Guillermo J.; Louis, Enrique (1998). Smoothness Implies Determinism in Time Series: A Measure Based Approach. Physical Review Letters, 81(20), 4345–4348. doi:10.1103/PhysRevLett.81.4345

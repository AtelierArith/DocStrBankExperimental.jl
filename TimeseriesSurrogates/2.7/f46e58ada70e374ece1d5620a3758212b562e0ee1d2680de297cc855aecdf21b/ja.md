```
PartialRandomization(α = 0.5)
```

`PartialRandomization` サロゲート[^Ortega1998] は [`RandomFourier`](@ref) フェーズサロゲートに似ていますが、フェーズのランダム化ステップ中に、フェーズを `[0, 2π]` から引くのではなく、フェーズは `[0, 2π]*α` から引かれます。ここで `α ∈ [0, 1]` です。著者は `α` をフェーズランダム化の「度合い」と呼び、`α = 0` は `0 %` のランダム化を意味し、`α = 1` は `100 %` のランダム化を意味します。

代替の部分ランダム化アルゴリズムについては、[`RelativePartialRandomization`](@ref) と [`SpectralPartialRandomization`](@ref) を参照してください。

[^Ortega1998]: Ortega, Guillermo J.; Louis, Enrique (1998). Smoothness Implies Determinism in Time Series: A Measure Based Approach. Physical Review Letters, 81(20), 4345–4348. doi:10.1103/PhysRevLett.81.4345

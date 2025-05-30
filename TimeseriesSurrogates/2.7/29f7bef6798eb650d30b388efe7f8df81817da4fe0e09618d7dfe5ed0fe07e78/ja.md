```
SpectralSpectralPartialRandomization(α = 0.5)
```

`SpectralPartialRandomization` サロゲートは [`PartialRandomization`](@ref) フェーズサロゲートに似ていますが、`[0, 2π]` から均等にフェーズを引く代わりに、パワーの割合 `α` に責任を持つ最高周波数成分のフェーズが `[0, 2π]` から引かれたランダムフェーズに置き換えられます。

部分的ランダム化アルゴリズムの詳細な比較については、ドキュメントを参照してください。

```
RelativePartialRandomization(α = 0.5)
```

`RelativePartialRandomization` サロゲートは [`PartialRandomization`](@ref) フェーズサロゲートに似ていますが、フェーズを `[0, 2π]` から均等に引くのではなく、フェーズは `ϕ + [0, 2π]*α` から引かれます。ここで、`α ∈ [0, 1]` であり、`ϕ` は元のフーリエフェーズです。

部分的ランダム化アルゴリズムの詳細な比較については、ドキュメントを参照してください。

```
WindingNumberJacobson(; geometry=nothing, winding_number_factor=sqrt(eps()),
                      hierarchical_winding=false)
```

[Jacobson2013](@cite)によって提案された複雑なジオメトリの内外セグメンテーションのアルゴリズム。

# キーワード

  * `geometry`: [`load_geometry`](@ref)によって返される複雑なジオメトリであり、`hierarchical_winding=true`を使用する場合にのみ必要です。
  * `hierarchical_winding`: `true`に設定すると、最適化された階層的アプローチが使用され、速度が大幅に向上します。詳細については[Hierarchical Winding](@ref hierarchical_winding)を参照してください。
  * `winding_number_factor`: 漏れのあるジオメトリの場合、`0.4`の係数がより良い内外セグメンテーションを提供します。

!!! warning "実験的な実装"
    これは実験的な機能であり、今後のリリースで変更される可能性があります。


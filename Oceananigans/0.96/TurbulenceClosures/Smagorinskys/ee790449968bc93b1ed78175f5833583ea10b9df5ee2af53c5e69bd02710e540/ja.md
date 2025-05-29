```
Smagorinsky([time_discretization::TD = ExplicitTimeDiscretization(), FT=Float64;]
            coefficient = 0.16,
            Pr = 1.0)
```

`Smagorinsky`型を返します。この型は、[Smagorinsky1958](@citet)および[Smagorinsky1963](@citet)によって提案された乱流閉じ込めに関連しており、渦粘性は次の形を持ちます。

```
νₑ = (Cˢ * Δᶠ)² * √(2Σ²)
```

また、渦拡散率は次の形を持ちます。

```
κₑ = νₑ / Pr.
```

ここで、`Δᶠ`はフィルタ幅、`Σ² = ΣᵢⱼΣᵢⱼ`はひずみテンソル`Σᵢⱼ`の二重ドット積、`Pr`は乱流プラントル数、`N²`は全体の浮力勾配、`Cb`は渦粘性に対するリチャードソン数の修正を掛ける定数です。

`Cˢ`はスモガリンスキー係数で、デフォルト値は0.16です。これは、[Lilly66](@citet)による分析に基づいています。他のオプションについては、`LillyCoefficient`および`DynamicCoefficient`を参照してください。

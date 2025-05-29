```
TranslationGroup{𝔽,T}
```

翻訳群 $\mathcal T(n)$ は、いくつかの [`Euclidean`](@extref `Manifolds.Euclidean`) 空間上の [`AdditionGroupOperation`](@ref) からなるリー群です。

# コンストラクタ

```
TranslationGroup(n₁,...,nᵢ; kwargs...)
```

$$
𝔽^{n₁,…,nᵢ}
$$

= `Euclidean(n₁,...,nᵢ; field=𝔽)` 上の翻訳群を生成します。これは群自体と同型です。`kwargs...` のすべてのキーワード引数は、[`Euclidean`](@extref `Manifolds.Euclidean`) にも渡されます。

私たちは、$\mathcal T(n)$ のリー代数を $\mathfrak t(n)$ と表記します。

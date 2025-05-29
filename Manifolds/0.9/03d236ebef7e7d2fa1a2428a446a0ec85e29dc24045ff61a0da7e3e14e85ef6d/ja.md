```
TranslationGroup{T,𝔽} <: GroupManifold{Euclidean{T,𝔽},AdditionOperation}
```

翻訳群 $\mathrm{T}(n)$ は翻訳配列によって表されます。

# コンストラクタ

```
TranslationGroup(n₁,...,nᵢ; field=𝔽, parameter::Symbol=:type)
```

$$
𝔽^{n₁,…,nᵢ}
$$

= `Euclidean(n₁,...,nᵢ; field=𝔽)` 上の翻訳群を生成します。これは群自体と同型です。

```
NelderMead(M::AbstractManifold, f [, population::NelderMeadSimplex])
```

コスト関数 `f` に対するネルダー・ミード最小化問題を多様体 `M` 上で解きます。初期集団 `population` が指定されていない場合は、ランダムな点のセットが選択されます。指定されている場合は、`population` の代わりに計算が行われます。

詳細なオプションについては [`NelderMead`](@ref) を参照してください。

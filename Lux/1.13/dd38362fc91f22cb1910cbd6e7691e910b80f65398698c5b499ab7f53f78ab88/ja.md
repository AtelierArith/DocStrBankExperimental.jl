```
recursive_make_zero(x)
```

ネストされた構造 `x` のゼロ値を再帰的に作成します。これは `fmap(zero, x)` を行うのと同等ですが、この実装は一般的なケースに対して型安定なコードを使用しています。

詳細は [`Lux.recursive_make_zero!!`](@ref) を参照してください。

!!! warning "非推奨警告"
    Lux v1.3.0 から、この関数は `Functors.fmap` に代わって非推奨となります。Functors v0.5 は `fmap` のパフォーマンスを大幅に改善しましたので、この関数は非推奨となりました。ユーザーは代わりに `Functors.fmap` を使用することを推奨します。


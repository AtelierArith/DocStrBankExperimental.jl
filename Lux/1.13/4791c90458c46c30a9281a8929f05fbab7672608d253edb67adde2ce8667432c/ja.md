```
recursive_make_zero!!(x)
```

ネストされた構造 `x` のゼロ値を再帰的に作成します。インプレースでゼロにできる葉は、その場で変更されます。

完全にアウトオブプレースのバージョンについては、[`Lux.recursive_make_zero`](@ref)を参照してください。

!!! warning "非推奨警告"
    Lux v1.3.0から、この関数は`Functors.fmap`の代わりに非推奨となります。Functors v0.5は`fmap`のパフォーマンスを大幅に改善しましたので、この関数は非推奨となりました。ユーザーは代わりに`Functors.fmap`を使用することを推奨します。


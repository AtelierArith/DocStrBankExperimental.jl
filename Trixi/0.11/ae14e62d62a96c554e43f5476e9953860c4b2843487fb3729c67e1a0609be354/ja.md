```
AnalysisCallbackCoupled(semi, callbacks...)
```

複数の分析コールバックを [`SemidiscretizationCoupled`](@ref) を用いた結合シミュレーションのために組み合わせます。各結合システムに対して、個別の [`AnalysisCallback`](@ref) **を** 作成し、`AnalysisCallbackCoupled` **に順番に** 渡す必要があります。つまり、個別の半離散化が `SemidiscretizationCoupled` に格納されているのと同じ順序で渡す必要があります。

!!! warning "実験的なコード"
    これは実験的な機能であり、いつでも変更される可能性があります。


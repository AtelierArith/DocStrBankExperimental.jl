```
fit(Mod::Type{<:StatisticalModel}, f::FormulaTerm, data, args...;
    contrasts::Dict{Symbol}, kwargs...)
```

テーブルデータを数値応答ベクトルと予測子行列に変換し、式 `f` を使用して指定されたモデルタイプを `fit` し、結果を [`TableRegressionModel`](@ref) または [`TableStatisticalModel`](@ref) （適切に）でラップします。

これは、`StatsAPI.StatisticalModel` のサブタイプであるモデルタイプを実装するモデリングパッケージのためのバックストップとして意図されていますが、完全な StatsModels の用語ベースのインターフェースを明示的にサポートしていません。 現在、これは式とデータから [`ModelFrame`](@ref) を作成し、次にこれを [`ModelMatrix`](@ref) に変換することによって機能しますが、これは内部実装の詳細であり、近い将来に変更される可能性があります。

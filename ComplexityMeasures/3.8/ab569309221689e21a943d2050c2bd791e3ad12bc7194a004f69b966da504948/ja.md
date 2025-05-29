```
InformationMeasureEstimator{I <: InformationMeasure}
```

すべての情報測定推定器のスーパークラスです。その直接のサブタイプは [`DiscreteInfoEstimator`](@ref) と [`DifferentialInfoEstimator`](@ref) です。

すべての推定器は何らかの方法で測定定義を参照する必要があるため、以下のインターフェースの決定を行いました：

1. すべての推定器は最初の型パラメータとして `I <: InformationMeasure` を持つ
2. すべての推定器は `definition` フィールドで情報測定を参照する
3. すべての推定器は `Base.@kwdef` を使用して定義され、`Estimator(; definition = Shannon())`（または他の任意のもの）という構文で初期化できる

具体的なサブタイプは上記に従う必要があります。例えば：

```julia
Base.@kwdef struct MyEstimator{I <: InformationMeasure, X} <: DiscreteInfoEstimator{I}
    definition::I
    x::X
end
```

!!! info "なぜ測定の*定義*を測定の*推定器*から分離するのか？"
    実際のアプリケーションでは、さまざまなエントロピーやエクストロピーの定義を計算するために必要な基礎となる確率質量関数や密度にアクセスできないことが一般的です。したがって、これらの情報測定は有限データから*推定*される必要があります。特定の測定（例： [`Shannon`](@ref) エントロピー）を推定する方法はいくつかあり、それぞれに利点と欠点があります。私たちは、さまざまな情報測定の文献推定器の完全なライブラリを提供することを目指しています（PRは歓迎です！）。


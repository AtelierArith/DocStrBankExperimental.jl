```
auto_arima(y::Vector{Fl};
           seasonal::Int = 0,
           max_p::Int = 5,
           max_q::Int = 5,
           max_P::Int = 2,
           max_Q::Int = 2,
           max_d::Int = 2,
           max_D::Int = 1,
           max_order::Int = 5,
           information_criteria::String = "aicc",
           allow_mean::Bool = true,
           show_trace::Bool = false,
           integration_test::String = "kpss",
           seasonal_integration_test::String = "seas"
           ) where Fl
```

最適な情報基準に従って最適な [`SARIMA`](@ref) モデルを自動的にフィットします。

# TODO 例を書く

# 参考文献

  * Hyndman, RJ and Khandakar.

自動時系列予測: Rのためのforecastパッケージ。統計ソフトウェアジャーナル, 26(3), 2008.

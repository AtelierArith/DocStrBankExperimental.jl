```
gewekediag(x::AbstractVector{<:Real}; first::Real=0.1, last::Real=0.5, kwargs...)
```

サンプル `x` の `first` および `last` の割合から Geweke 診断 [^Geweke1991] を計算します。

この診断は、自己相関のあるサンプルで推定された事後平均の収束を評価するために設計されています。最初と最後のイテレーションの割合を含む2つのウィンドウ内のサンプル平均を比較する正規ベースの検定統計量を計算します。ユーザーは、2つのウィンドウの間に十分な分離があることを確認し、サンプルが独立であると仮定できるようにする必要があります。有意でない検定 p 値は収束を示します。有意な p 値は非収束を示し、初期サンプルをバーンインシーケンスとして破棄する必要があるか、追加のサンプルをシミュレートする必要がある可能性を示します。

`kwargs` は [`mcse`](@ref) に転送されます。

[^Geweke1991]: Geweke, J. F. (1991). Evaluating the accuracy of sampling-based approaches to the calculation of posterior moments (No. 148). Federal Reserve Bank of Minneapolis.

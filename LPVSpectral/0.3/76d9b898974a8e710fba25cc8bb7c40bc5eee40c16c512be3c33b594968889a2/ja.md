`x,f = ls_spectral(y,t,f=(0:((length(y)-1)/2))/length(y); λ=0)`

最小二乗法を使用してスペクトル推定を行います。`y`は分析対象の信号で、`t`はサンプリングポイント、`f`は周波数のベクトルです。

`ls_spectral`と`rfft`の違いは`abs.(rfft) = √(2π)abs.(x)`です。

また、`ls_sparse_spectral`や`tls_spectral`も参照してください。

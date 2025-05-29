`ls_windowcsd(y,u,t,freqs; nw = 10, noverlap = -1, window_func=rect, estimator=ls_spectral, kwargs...)`

ウィンドウ付き交差スペクトル密度推定を最小二乗法を用いて行います。

`y` と `u` は分析される2つの信号で、`t::AbstractVector` はそれらのサンプリングポイントです。`window_func` のデフォルトは `Windows.rect` です。

`estimator` は使用するスペクトル推定関数で、デフォルトは `ls_spectral` です。スパース推定には、`estimator = ls_sparse_spectral` を試してください。詳細については `ls_sparse_spectral` を参照してください。

追加のヘルプについては `ls_spectral` を参照してください。

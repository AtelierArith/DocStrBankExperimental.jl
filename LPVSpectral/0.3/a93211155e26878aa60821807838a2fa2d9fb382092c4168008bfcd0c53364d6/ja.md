`S,f = ls_windowpsd(y,t,freqs; nw = 8, noverlap = -1, window_func=rect, estimator=ls_spectral, kwargs...)`

最小二乗法を使用してウィンドウ付きスペクトル推定を行います。 `window_func` のデフォルトは `Windows.rect` です。

`estimator` は使用するスペクトル推定関数で、デフォルトは `ls_spectral` です。スパース推定には、`estimator = ls_sparse_spectral` を試してください。詳細については `ls_sparse_spectral` を参照してください。 `kwargs` は `estimator` に渡されます。

追加のヘルプについては `ls_spectral` を参照してください。

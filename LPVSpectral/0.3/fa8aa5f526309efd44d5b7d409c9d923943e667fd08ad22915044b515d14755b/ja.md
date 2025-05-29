`ls_cohere(y,u,t,freqs; nw = 10, noverlap = -1, estimator=ls_spectral, kwargs...)`

最小二乗法を使用してスペクトルコヒーレンス推定を行います。

`estimator` は使用するスペクトル推定関数で、デフォルトは `ls_spectral` です。スパース推定には、`estimator = ls_sparse_spectral` を試してください。詳細については `ls_sparse_spectral` を参照してください。また、追加のヘルプについては `ls_windowcsd` と `ls_spectral` も参照してください。

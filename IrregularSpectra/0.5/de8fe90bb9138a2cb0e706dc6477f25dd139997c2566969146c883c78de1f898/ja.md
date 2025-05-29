`estimate_sdf(pts::Vector{Float64}, data, g; Ω=default_Ω(pts, g),              frequencies=default_frequencies(pts, g, Ω),              wts=nothing, kwargs...) -> (frequencies, estimates)`

指定された位置 `pts` でサンプリングされた定常過程のスペクトル密度を、`data` によって与えられた値と周波数 `frequencies` で推定します。`data` の各列は過程の独立同分布サンプルとして扱われ、最終的な推定器で平均化されます。`Ω` はウィンドウの数値積分重みの解像度の最大値です。

提供されたキーワード引数は、`wts` が `nothing` の場合に `window_quadrature_weights` に渡され、`wts` が提供されている場合は無視されます。利用可能なキーワード引数の詳細については、`window_quadrature_weights` のドキュメントを参照してください。`wts` が提供されている場合、`Ω` 引数も何もしません。

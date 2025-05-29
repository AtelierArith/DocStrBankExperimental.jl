```
distance_profile(dist, Q, T; kwargs...)
```

スライディング `Q` を `T` に対して移動させ、`dist` を使用して時間ウィンドウ間の距離を測定する距離プロファイルを計算します。

出力は `length(T) - length(Q) + 1` の長さのベクトルです。入力が行列または高次元配列の場合、時間は最後の軸と見なされ、`T[:, t:t+lastlength(Q)-1]` の形式のウィンドウが比較されます。ここで、`lastlength` は最後の軸に沿った長さを測定します。

キーワード引数は `dist` に送信され、次のように呼び出されます `dist(Q,T; kwargs...)`。`dist` は関数または Distances.jl からの距離であることができます。

`distance_profile!(D, dist, Q, T; kwargs...)` はインプレースバージョンです。

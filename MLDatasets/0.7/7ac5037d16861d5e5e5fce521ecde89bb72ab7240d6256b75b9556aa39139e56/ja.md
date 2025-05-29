```
PEMSBAY(; num_timesteps_in::Int = 12, num_timesteps_out::Int=12, dir=nothing, normalize = true)
```

PEMS-BAYデータセットは、[Diffusion Convolutional Recurrent Neural Network: Data-Driven Traffic Forecasting](https://arxiv.org/abs/1707.01926)論文で説明されています。これは、カリフォルニア交通局（Cal-Trans）のパフォーマンス測定システム（PeMS）によって収集されました。

`PEMSBAY`は、ベイエリアの交通センサーを表す325のノードを持つグラフです。

エッジの重み`w`は、`edge_data`の特徴配列に含まれており、センサー間の距離を表します。

ノードの特徴は、交通速度とセンサーによって収集された測定の時間であり、`num_timesteps_in`の時間ステップに分割されています。

ターゲット値は、センサーによって収集された測定の交通速度であり、`num_timesteps_out`の時間ステップに分割されています。

`normalize`フラグは、データがZスコア正規化を使用して正規化されるかどうかを示します。

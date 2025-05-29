```
sample_skeleton(): PDMPサンプラーからスケルトンを抽出する．

Parameters:
- n_sk (Int): 生成するスケルトンサンプルの数。
- xinit (Array{Float64, 1}): 粒子の初期位置。
- vinit (Array{Float64, 1}): 粒子の初期速度。
- seed (Int): 乱数生成のためのシード値。
- verbose (Bool): サンプリング中に進行状況バーを表示するかどうか。デフォルトはtrue。

Returns:
- output: サンプリングプロセスの出力状態。
```

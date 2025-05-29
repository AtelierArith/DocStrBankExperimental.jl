```
sample()：PDMPSampler からサンプルをするための関数．
sample_skeleton() と sample_from_skeleton() の wrapper．

Args:
    N_sk (Int): 生成するスケルトンポイントの数。
    N_samples (Int): スケルトンから生成する最終サンプルの数。
    xinit (Array{Float64, 1}): 初期位置。
    vinit (Array{Float64, 1}): 初期速度。
    seed (Int): 乱数生成のためのシード。
    verbose (Bool, optional): 進行状況情報を表示するかどうか。デフォルトは true。

Returns:
    Array{Float64, 2}: PDMP モデルから生成されたサンプルの配列。
```

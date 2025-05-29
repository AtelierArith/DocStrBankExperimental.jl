```
SolitaryWaveSerreGreenNaghdi(param; x₀=0)
```

指定された速度を持つSerre-Green-Naghdi孤立波を計算します。

# 引数

  * `param :: NamedTuple`: 速度 `c` と無次元パラメータ `ϵ` と `μ`、メッシュサイズ `L` とコレクションポイントの数 `N` を含む問題のパラメータ;
  * `x₀ :: Real`: (キーワード、オプション、デフォルト = 0) 孤立波の中心。

# 戻り値

`(η,u,v,mesh)` には

  * `η :: Vector{Float64}`: 表面変形;
  * `u :: Vector{Float64}`: 層平均速度;
  * `v :: Vector{Float64}`: 表面での速度ポテンシャルのトレースの導関数;
  * `mesh :: Mesh`: メッシュコレクションポイント。

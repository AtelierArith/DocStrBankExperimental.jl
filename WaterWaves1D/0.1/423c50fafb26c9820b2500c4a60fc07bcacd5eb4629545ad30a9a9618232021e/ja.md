```
CnoidalWaveSerreGreenNaghdi(param; P=1)
```

指定された `h₀<h₁<h₂` のセレ-グリーン-ナグディのコノイダル波を計算します。`h₁` は最小値で、`h₂` は波の最大値です。`h₀ -> h₁` のとき、コノイダル波は孤立波に収束します。例えば、[Gavrilyuk, Nkonga, Shyue and Truskinovsky](https://doi.org/10.1088/1361-6544/ab95ac) を参照してください。

# 引数

  * `param :: NamedTuple`: `h₀<h₁<h₂` と無次元パラメータ `ϵ` と `μ`、およびコレクションポイントの数 `N` を含む問題のパラメータ。
  * `P :: Int`: (キーワード、オプション、デフォルト = 1) 構築されたメッシュ内のコノイダル波の周期数。

# 戻り値

`(η,u,v,mesh,param)` で、

  * `η :: Vector{Float64}`: 表面変形;
  * `u :: Vector{Float64}`: 層平均速度;
  * `v :: Vector{Float64}`: 表面での速度ポテンシャルのトレースの導関数;
  * `mesh :: Mesh`: メッシュコレクションポイント;
  * `param :: NamedTuple`: 有用なパラメータ

```

```
heartbeat = HeartBeat(circumferential_strain, radial_strain, longitudinal_strain)
```

HeartBeat構造体。円周方向、放射方向、縦方向の3種類のひずみに特徴づけられた心拍のような動きを生成します。

# 引数

  * `circumferential_strain`: (`::Real`) 縮小パラメータ
  * `radial_strain`: (`::Real`) 縮小パラメータ
  * `longitudinal_strain`: (`::Real`) 縮小パラメータ

# 戻り値

  * `heartbeat`: (`::HeartBeat`) HeartBeat構造体

# 例

```julia-repl
julia> heartbeat = HeartBeat(circumferential_strain=-0.3, radial_strain=-0.2, longitudinal_strain=0.0)
```

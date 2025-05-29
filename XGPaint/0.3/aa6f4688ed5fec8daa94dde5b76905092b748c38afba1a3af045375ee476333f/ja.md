```
paint!(result_map, nu_obs, model, sources, fluxes_cen, fluxes_sat)
```

ソースカタログをマップに描画し、`fluxes_cen` と `fluxes_sat` にフラックスを記録します。

# 引数:

  * `result_map::HealpixMap{T_map, RingOrder}`: 描画するHealpixマップ
  * `nu_obs`: 周波数（Hz）
  * `model::AbstractCIBModel{T}`: ソースモデルパラメータ
  * `sources`: generate_sourcesからのソース情報を含むNamedTuple
  * `fluxes_cen::AbstractArray`: セントラルのフラックスを書き込むためのバッファ
  * `fluxes_sat::AbstractArray`: 衛星のフラックスを書き込むためのバッファ

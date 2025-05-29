```
paint!(result_map, model, sources, min_redshift, max_redshift)
```

LRGカタログをマップに「ペイント」します。

# 引数:

  * `result_map::HealpixMap{T_map, RingOrder}`: ペイントするHealpixマップ
  * `model::AbstractCIBModel{T}`: ソースモデルパラメータ
  * `sources`: generate_sourcesからのソース情報を含むNamedTuple
  * `fluxes_cen::AbstractArray`: セントラルのフラックスを書き込むためのバッファ
  * `fluxes_sat::AbstractArray`: サテライトのフラックスを書き込むためのバッファ

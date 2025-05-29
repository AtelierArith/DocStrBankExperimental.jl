```
generate_sources(model, cosmo, halo_pos_inp, halo_mass_inp; verbose=true)
```

モデルとハローカタログからソースカタログを生成します。これはハロー配列を`model`で指定された型に変換します。

# 引数:

  * `model::AbstractCIBModel{T}`: ソースモデルパラメータ
  * `cosmo::Cosmology.FlatLCDM{T}`: 背景宇宙論
  * `Healpix_res::Resolution`: Healpixマップ解像度
  * `halo_pos_inp::AbstractArray{TH,2}`: ハロー位置 (3, nhalos) の次元を持つ
  * `halo_mass_inp::AbstractArray{TH,1}`: ハロー質量

# キーワード

  * `verbose::Bool=true`: 進行状況の詳細を出力する

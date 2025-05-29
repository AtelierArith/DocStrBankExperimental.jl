ReconstructMap(path_ref::String)

コイル感度マップをMRIReco.jl関数を使用して再構築します。

# 引数

  * `path_rep::String` - ISMRMRD形式の参照データのパス
  * `thresh::Float64` - マスキングしきい値: マスクサイズを縮小するには増加させ、拡張するには減少させます

MRIRecoの参考文献: https://onlinelibrary.wiley.com/doi/epdf/10.1002/mrm.28792 ISMRMRDの参考文献: https://onlinelibrary.wiley.com/doi/epdf/10.1002/mrm.26089

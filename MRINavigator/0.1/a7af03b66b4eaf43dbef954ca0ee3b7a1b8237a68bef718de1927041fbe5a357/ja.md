```
ReconstructSaveMap(path_nifti::String, path_ref::String, thresh::Float64)
```

MRIReco.jl関数を使用してコイル感度マップを再構築し、空間情報なしでnifti形式で保存します。

# 引数

  * `path_nifti::String` - niftiファイルのパス。ファイルは.nii拡張子を持っている必要があります
  * `path_rep::String` - ISMRMRD形式の参照データのパス
  * `thresh::Float64` - マスキングしきい値：マスクサイズを縮小するには増加させ、マスクサイズを拡大するには減少させます

MRIRecoの参考文献: https://onlinelibrary.wiley.com/doi/epdf/10.1002/mrm.28792 ISMRMRDの参考文献: https://onlinelibrary.wiley.com/doi/epdf/10.1002/mrm.26089

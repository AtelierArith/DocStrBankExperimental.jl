```
niftiSaveImg(img::AbstractArray{T}, acq::AcquisitionData, path_nifti::String)
```

再構成出力のモジュールをnifti形式で保存します。空間情報は含まれません。

# 引数

  * `img::AbstractArray{T}` - 再構成出力
  * `acq::AcquisitionData` - ボクセル寸法を保存するために必要な再構成入力 (MRIReco.jl)
  * `path_nifti::String` - niftiファイルのパス。ファイルは.nii拡張子を持っている必要があります

MRIRecoの参考文献: https://onlinelibrary.wiley.com/doi/epdf/10.1002/mrm.28792

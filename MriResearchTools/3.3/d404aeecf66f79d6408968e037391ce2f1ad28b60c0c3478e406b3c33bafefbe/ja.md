```
getsensitivity(mag; sigma, nbox=15)

getsensitivity(mag, pixdim; sigma_mm=7, nbox=15)

getsensitivity(mag::NIVolume, datatype=eltype(mag); sigma_mm=7, nbox=15)
```

`boxsegment`アプローチを使用してバイアスフィールドを計算します。これは、オブジェクトのほとんどの領域に存在する「主要な組織」があると仮定しています。設定されていない場合、sigma*mmはデフォルトで7mm、最大10%のFoVになります。sigma*mmの値はバイアスフィールドに対応する必要があり、急速に変化するバイアスフィールドの場合はこれを小さくする必要があります。 [CLEAR-SWI](https://doi.org/10.1016/j.neuroimage.2021.118175)に発表されています。

[`makehomogeneous`](@ref)も参照してください。

```
strainvdet(::Type{DeforModelRed2DStrain},  Cv::Vector{T}) where {T}
```

対称ひずみのような正方行列をベクトルとして表現した行列式を計算します。せん断ひずみ成分は行列表現のエントリの2倍であることを忘れないでください。

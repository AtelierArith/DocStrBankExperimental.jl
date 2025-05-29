```
LocalMultistartFit(DM::AbstractDataModel, scale::Real=sqrt(InvChisqCDF(DOF(DM), ConfVol(2.0))); kwargs...)
LocalMultistartFit(DM::AbstractDataModel, mle::AbstractVector{<:Number}, scale::Real=sqrt(InvChisqCDF(DOF(DM), ConfVol(2.0))); kwargs...)
```

与えられたMLEの周りで、フィッシャー情報から構築された立方体内でローカルにマルチスタート検索を実行し、`scale`で乗算します。

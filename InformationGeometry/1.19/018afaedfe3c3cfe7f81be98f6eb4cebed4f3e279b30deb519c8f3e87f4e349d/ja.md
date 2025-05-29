```
FindConfBoundaryOnPlane(DM::AbstractDataModel,PL::Plane,Confnum::Real=1.; tol::Real=1e-8) -> Union{AbstractVector{<:Number},Bool}
```

平面 `PL` 内の点を計算し、信頼度領域の境界に位置する。この信頼度はレベル `Confnum` です。そのような点が見つからない場合（つまり、存在しないように見える場合）、メソッドは `false` を返します。

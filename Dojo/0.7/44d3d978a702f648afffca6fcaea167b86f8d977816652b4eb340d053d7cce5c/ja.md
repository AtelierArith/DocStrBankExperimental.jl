```
NonlinearContact{T,N} <: Contact{T,N}

衝突と摩擦のための非線形摩擦円錐を持つ接触オブジェクト

friction_coefficient: 摩擦係数の値
contact_tangent: ワールドフレームから表面接線フレームへのマッピング
contact_normal: contact_tangentの逆/補完
contact_origin: 質量中心に対するボディ上の接触位置
contact radius: 接触半径
```

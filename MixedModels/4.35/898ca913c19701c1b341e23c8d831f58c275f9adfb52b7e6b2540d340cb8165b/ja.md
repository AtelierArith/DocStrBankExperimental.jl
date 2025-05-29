```
issingular(m::MixedModel, θ=m.θ; atol::Real=0, rtol::Real=atol>0 ? 0 : √eps)
```

モデル `m` がパラメータベクトル `θ` に対して特異かどうかをテストします。

等号比較が使用されるのは、`fit!` で小さな非負の θ 値が 0 に置き換えられるためです。

!!! note
    `GeneralizedLinearMixedModel` の場合、デフォルトが使用されない場合は、全てのパラメータベクトル（`fast=false` の場合の β を含む）を指定する必要があります。


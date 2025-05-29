```
two_ray_propagation( distance::Real, transmit_height::Real, receive_height::Real, frequency_hz::Real, Γ::Real )::Complex
```

平面上の2点間の双方向2レイ伝播を計算します。伝播因子Fを返します。片道の電力伝播因子は|F|²です。

# 引数

  * `distance`       	平面地球に平行な距離。
  * `transmit_height`	平面地球上の送信機の高さ。
  * `receive_height` 	平面地球上の受信機/ターゲットの高さ。
  * `Γ`             	平面地球の媒質の反射係数。

## 例

```jldoctest
julia> res = two_ray_propagation( 2e3, 10, 12, 20e9, -1 );

julia> round(res, digits=6)
1.999395 + 0.034791im
```

## 参考文献

  * Radar Systems Engineering Lecture 5 Propagation through the Atmosphere, IEEE New Hampshire Section IEEE AES Society, 2010

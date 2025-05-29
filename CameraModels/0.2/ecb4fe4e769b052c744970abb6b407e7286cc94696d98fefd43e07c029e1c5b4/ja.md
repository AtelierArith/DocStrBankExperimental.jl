```julia
project(model, r_P; c_T_r)

```

世界のシーンを画像に投影します。

実世界の座標をカメラ座標に変換する変換を返します。これは現在、レンズと画像平面の間の接線歪みを無視しています。

ノート

  * `r_P` はカメラの参照フレームに変換された参照フレーム内の点です：

      * `c_P = c_T_r * r_P`

非推奨:

  * yakir12: `point2pixel`: @deprecate point2pixel(model, pt) project(model, pt[[1;3;2]])

また見てください: [`backproject`](@ref)

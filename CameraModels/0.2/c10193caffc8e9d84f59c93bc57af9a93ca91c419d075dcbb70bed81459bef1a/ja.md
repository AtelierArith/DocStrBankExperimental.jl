```julia
backproject(model, px_coord)

```

画像から世界シーンへのバックプロジェクション。

実世界の座標をカメラ座標に変換する変換を返します。これは現在、レンズと画像平面の間の接線歪みを無視しています。

非推奨:

  * yakir12: `pixel2ray`: @deprecate pixel2ray(model, px) backproject(model, px)[[1;3;2]]

また見てください: [`project`](@ref)

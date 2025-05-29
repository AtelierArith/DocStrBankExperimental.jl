```
integratefunction(
    self::AbstractFEMM,
    geom::NodalField{GFT},
    fh::F;
    initial::R = zero(typeof(fh(zeros(ndofs(geom), 1)))),
    m = -1,
) where {GFT<:Number, F<:Function, R<:Number}
```

離散多様体上で関数を積分します。

幾何学的セル上でスカラー関数を積分します。この関数は、位置ベクトルを引数として取ります。

スカラー関数が単に +1 を返す場合（例えば `(x) ->  1.0` のように）、結果は体積（点の数、長さ、面積、3次元体積など、多様体の次元に応じて）を測定します。関数が質量密度を返す場合、このメソッドは質量を測定し、関数が x 座標を返す場合は y 軸に関する静的モーメントを測定します。

# 例:

メッシュの体積を計算し、その重心を求めます：

```
V = integratefunction(femm, geom, (x) ->  1.0, 0.0)
Sx = integratefunction(femm, geom, (x) ->  x[1], 0.0)
Sy = integratefunction(femm, geom, (x) ->  x[2], 0.0)
Sz = integratefunction(femm, geom, (x) ->  x[3], 0.0)
CG = vec([Sx Sy Sz]/V)
```

原点に対するメッシュの慣性モーメントを計算します：

```
Ixx = integratefunction(femm, geom, (x) ->  x[2]^2 + x[3]^2)
```

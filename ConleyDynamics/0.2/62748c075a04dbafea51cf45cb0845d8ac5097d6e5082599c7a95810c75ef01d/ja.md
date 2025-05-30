```
plot_planar_cubical(cc::LefschetzComplex,
                    fname::String;
                    [hfac::Real=1.2,]
                    [vfac::Real=1.2,]
                    [cubefac::Real=0,]
                    [pdim::Vector{Bool}=[true,true,true],]
                    [pv::Bool=false])
```

平面立方体複合体の画像を作成します。

これは、頂点座標の指定を必要としない代替方法です。座標は立方体の頂点ラベルから取得されます。

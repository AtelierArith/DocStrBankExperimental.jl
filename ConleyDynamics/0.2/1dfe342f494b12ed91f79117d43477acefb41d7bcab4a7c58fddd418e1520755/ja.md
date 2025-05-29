```
plot_planar_cubical_morse(cc::LefschetzComplex,
                          fname::String,
                          morsesets::CellSubsets;
                          [hfac::Real=1.2,]
                          [vfac::Real=1.2,]
                          [cubefac::Real=0,]
                          [pdim::Vector{Bool}=[false,true,true],]
                          [pv::Bool=false])
```

平面立方体複体の画像を作成し、モース集合や選択された多重ベクトルも表示します。

これは、頂点座標の指定を必要としない代替方法です。座標は立方体の頂点ラベルから取得されます。

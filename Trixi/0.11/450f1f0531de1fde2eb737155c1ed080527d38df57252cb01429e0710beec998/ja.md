```
AveragingCallback(semi::SemidiscretizationHyperbolic, tspan; output_directory="out",
                  filename="averaging.h5")
```

!!! warning "実験的なコード"
    このコールバックは実験的であり、将来のリリースで変更される可能性があります。


`semi`によって記述された流れ場を平均化するコールバックであり、`semi`は二次元の圧縮性オイラー方程式の半離散化でなければなりません。このコールバックは、`tspan`で与えられた時間間隔の各ノードに対して平均速度、平均音速、平均密度、および平均渦度を記録し、結果を`output_directory`内のHDF5ファイル`filename`に保存します。このコールバックは適応メッシュ細分化（[`AMRCallback`](@ref)）をサポートしていないことに注意してください。

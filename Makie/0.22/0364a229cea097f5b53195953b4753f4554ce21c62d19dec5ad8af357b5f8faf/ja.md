```
convert_arguments(ct::GridBased, x::VecOrMat, y::VecOrMat, z::Matrix)
```

もし `ct` が `Heatmap` で、`x` と `y` がベクトルであれば、`x` と `y` の長さからそれらがヒートマップビンのエッジを表しているのか、センターを表しているのかを推測します。もしそれらがセンターであれば、エッジに変換します。エレメンタイプを `Float32` に変換し、出力を `Tuple` として返します。

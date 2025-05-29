```
diff_entropy_uniform(N::AbstractEcologicalNetwork, dims::I=nothing)
```

マージナルのエントロピーの差を、均一分布のエントロピーと比較して計算します。パラメータ `dims` は、どのマージナルが使用されるかを示し、値が提供されない場合は両方が使用されます。出力はビット単位です。

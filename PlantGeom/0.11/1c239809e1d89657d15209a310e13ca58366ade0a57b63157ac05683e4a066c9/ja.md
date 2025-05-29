```
write_opf(file, opf)
```

明示的なジオメトリを持つMTGをOPFファイルとしてディスクに書き込みます。

# 注意事項

ノード属性 `:geometry` は予約語として扱われ、その意味を知らずに使用すべきではありません。

# 例

```julia
using PlantGeom
file = joinpath(dirname(dirname(pathof(PlantGeom))),"test","files","simple_plant.opf")
opf = read_opf(file)
write_opf("test.opf", opf)
opf2 = read_opf("test.opf")
viz(opf2)
```

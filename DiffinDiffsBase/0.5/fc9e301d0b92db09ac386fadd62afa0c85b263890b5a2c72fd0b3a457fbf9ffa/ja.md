```
ilag!(panel::PanelStructure, l::Integer=1)
```

`panel`のすべてのid-timeの組み合わせに対する`l`番目の遅延値のインデックスのベクトルを返します。インデックスは、以前に収集されている場合は`panel`から取得されます。それ以外の場合は、[`findlag!`](@ref)を呼び出すことによって作成されます。[`ilead!`](@ref)も参照してください。

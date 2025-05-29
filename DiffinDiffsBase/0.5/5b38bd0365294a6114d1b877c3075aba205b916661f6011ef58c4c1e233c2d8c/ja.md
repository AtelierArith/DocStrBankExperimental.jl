```
ilead!(panel::PanelStructure, l::Integer=1)
```

`panel`のすべてのid-timeの組み合わせに対する`l`番目のリード値のインデックスのベクトルを返します。インデックスは、以前に収集されている場合は`panel`から取得されます。それ以外の場合は、[`findlead!`](@ref)を呼び出すことで作成されます。[`ilag!`](@ref)も参照してください。

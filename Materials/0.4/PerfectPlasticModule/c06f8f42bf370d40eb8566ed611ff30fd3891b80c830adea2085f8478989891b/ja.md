```
integrate_material!(material::GenericPerfectPlastic)
```

完璧なプラスチック材料：硬化なし。弾性領域は原点を中心に保たれ、元のサイズを保持します。

これは標準的な基本的な塑性モデルです。教科書を参照してください。例えば：

```
J. C. Simo, T. J. R. Hughes. Computational Inelasticity. Interdisciplinary
Applied Mathematics volume 7. Springer. 1998. http://dx.doi.org/10.1007/b98904

本の表記は私たちのものとは多少異なります。参照してください：
https://github.com/JuliaFEM/Materials.jl/pull/66#issuecomment-674786955
```

```
integrate_material!(material::GenericMemory{T}) where T <: Real
```

ひずみ記憶効果を持つ材料モデル。

これは、運動的および等方的な硬化を伴う2つのバックストレスを持つChaboche材料に似ていますが、このモデルはひずみ記憶項も特徴としています。

ひずみ記憶は、ひずみ振幅依存の等方的硬化をモデル化するために使用されます。実際には、引張試験曲線からサイクリック挙動への遷移をこのモデルで捉えることができます。

参照：

```
D. Nouailhas, J.-L. Chaboche, S. Savalle, G. Cailletaud. On the constitutive
equations for cyclic plasticity under nonproportional loading. International
Journal of Plasticity 1(4) (1985), 317--330.
https://doi.org/10.1016/0749-6419(85)90018-X
```

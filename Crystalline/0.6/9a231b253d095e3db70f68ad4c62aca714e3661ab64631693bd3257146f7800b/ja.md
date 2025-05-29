```
ModulatedFourierLattice{D} <: AbstractFourierLattice{D}
```

`D`次元の具体的なフーリエ（平面波）格子であり、[`UnityFourierLattice{D}`](@ref)から、複素数によってその軌道係数をスケーリングおよび変調することによって導出されます。一般に、係数は単位ノルムを持たないことがあります。

```
abstract  AbstractSPMF <: ProjectableNEP
```

AbstractSPMFは、行列と関数の積の和として表現できるNEPを表す抽象クラスです。$M(λ)=Σ_i A_i f_i(λ)$の形を持ち、ここでi = 0,1,2,...であり、すべての行列はサイズ$n×n$で、$f_i$は関数です。

任意のAbstractSPMFは、関数と行列を返す[`get_Av()`](@ref)および[`get_fv()`](@ref)の実装を持たなければなりません。

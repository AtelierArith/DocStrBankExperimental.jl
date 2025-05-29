```
outgoing_spin_pols(proc_def::AbstractProcessDefinition)
```

散乱過程のためのインターフェース関数。与えられたプロセス定義に対するスピンまたは偏光のタプルを返します。順序は[`outgoing_particles`](@ref)から返される粒子と同じでなければなりません。デフォルトの実装が提供されており、すべての[`is_fermion`](@ref)に対して[`AllSpin`](@ref)を、すべての[`is_boson`](@ref)に対して[`AllPolarization`](@ref)を返します。

!!! note "パフォーマンス"
    この関数がコンパイル時に既知の値を返す場合、派生関数のパフォーマンスに非常に有益です。


参照: [`AbstractSpinOrPolarization`](@ref)

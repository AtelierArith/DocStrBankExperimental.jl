```
incoming_multiplicity(proc::AbstractProcessDefinition)
```

`proc`の入射粒子によって表されるスピンと偏光の組み合わせの数を返します。この関数は、`proc`のために[`incoming_spin_pols`](@ref)によって返される入射粒子のスピンと偏光のみを考慮します。

!!! note "入射および出射スピン/偏光"
    総多重度は、入射および出射の多重度を単純に掛け合わせたものではないことに注意してください。総プロセス多重度については、[`multiplicity`](@ref)を参照してください。


参照: [`SyncedPolarization`](@ref), [`SyncedSpin`](@ref), [`multiplicity`](@ref), [`outgoing_multiplicity`](@ref)

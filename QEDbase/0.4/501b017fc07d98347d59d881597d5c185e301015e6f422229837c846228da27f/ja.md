```
outgoing_multiplicity(proc::AbstractProcessDefinition)
```

`proc`の出力粒子によって表されるスピンと偏光の組み合わせの数を返します。この関数は、`proc`のために[`outgoing_spin_pols`](@ref)によって返される出力粒子のスピンと偏光のみを考慮します。

!!! note "入射および出力スピン/偏光"
    総多重度は、入射および出力の多重度を単純に掛け合わせたものではないことに注意してください。総プロセス多重度については、[`multiplicity`](@ref)を参照してください。


参照: [`SyncedPolarization`](@ref), [`SyncedSpin`](@ref), [`multiplicity`](@ref), [`incoming_multiplicity`](@ref)

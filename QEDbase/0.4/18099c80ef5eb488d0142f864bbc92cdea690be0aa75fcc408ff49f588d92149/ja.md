```
multiplicity(proc::AbstractProcessDefinition)
```

`proc` が表すスピンと偏光の組み合わせの総数を返します。これは、`proc` のために [`spin_pols`](@ref) が返す特定の [`AbstractSpinOrPolarization`](@ref) に依存します。例えば、4つの不定スピン/偏光を持つデフォルトのコンプトン過程は、2^4 = 16 の多重度を持ちます。同期した偏光を持つ多くの入射光子を持つコンプトン過程でも、多重度は依然として16です。

!!! note "パフォーマンス"
    [`incoming_spin_pols`](@ref) と [`outgoing_spin_pols`](@ref) がコンパイル時に評価できる限り、この関数は完全にコンパイルされます。


!!! note "入射および出射スピン/偏光"
    総多重度は、入射および出射の多重度を単純に掛け合わせたものではないことに注意してください。これは、入射粒子と出射粒子が互いに同期している場合に当てはまります。


参照: [`SyncedPolarization`](@ref), [`SyncedSpin`](@ref), [`incoming_multiplicity`](@ref), [`outgoing_multiplicity`](@ref)

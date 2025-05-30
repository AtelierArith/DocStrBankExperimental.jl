```
SyncedPolarization{N::Int} <: AbstractIndefinitePolarization
```

複数の粒子が同期した偏光を持つことを示す不定偏光タイプです。2つの偏光は、`N`の値が同じであるときに同期していると見なされます。これは、同じ`SyncedPolarization`を持つすべての粒子の結果の重複度が合計で2になることを意味します。

プロセスに単一の`SyncedPolarization{N}`があることは合法です。この場合、それは[`AllPolarization`](@ref)と同じように振る舞います。

参照: [`multiplicity`](@ref)

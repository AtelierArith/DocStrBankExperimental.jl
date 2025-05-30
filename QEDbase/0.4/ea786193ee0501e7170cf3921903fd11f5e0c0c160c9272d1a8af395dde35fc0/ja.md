```
SyncedSpin{N::Int} <: AbstractIndefiniteSpin
```

複数の粒子が同期したスピンを持つことを示す不定スピンタイプです。2つのスピンは、`N`の値が同じであるときに同期していると見なされます。これは、同じ`SyncedSpin`を持つすべての粒子に対して、結果の重複度が合計2になることを意味します。

プロセス内に単一の`SyncedSpin{N}`があることは合法です。この場合、それは[`AllSpin`](@ref)と同じように振る舞います。

参照: [`multiplicity`](@ref)

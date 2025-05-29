```
SpinWaveTheorySpiral(sys::System; k, axis, measure, regularization=1e-8)
```

[`SpinWaveTheory`](@ref)に類似していますが、提供されたシステムを一般化されたスパイラル秩序を持つものとして解釈します。この秩序は、非整合的である可能性のある単一の伝播波ベクトル `k` によって記述されます。`axis` ベクトルは、その表面法線を介して偏光面を定義します。通常、`sys` のスピン配置と伝播波ベクトル `k` は [`minimize_spiral_energy!`](@ref) を使用して最適化されます。それに対して、`axis` は通常、対称性の考慮から決定されます。

結果として得られるオブジェクトは、スピン波の [`dispersion`](@ref) を計算するためや、[`intensities_bands`](@ref) および [`intensities`](@ref) を介して構造因子を計算するために使用できます。

この計算のアルゴリズムは、[Toth and Lake, J. Phys.: Condens. Matter **27**, 166002 (2015)](https://arxiv.org/abs/1402.6069) で開発され、[SpinW コード](https://spinw.org/) に実装されています。

```
sys_from_particles(P, i)
sys_from_particles(P)
```

`Particles`係数を持つシステム `P` から `i` 番目のシステムを返します。

インデックスなしで呼び出すと、各可能な `i` に対して1つのシステムのベクトルを返します。

この関数は、`Particles` を使用した不確実な表現から、複数の `StateSpace` モデルを使用した「マルチモデル」表現に変換するために使用されます。

他にも [`ss2particles`](@ref)、[`mo_sys_from_particles`](@ref) および `MonteCarloMeasurements.nominal` を参照してください。

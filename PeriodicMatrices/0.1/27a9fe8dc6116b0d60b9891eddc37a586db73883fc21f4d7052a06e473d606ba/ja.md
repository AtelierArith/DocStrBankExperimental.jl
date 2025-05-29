```
pmmultraddsym(A, B, C, α, β)
```

対称周期行列 `α*A + β*B'*C` を計算します。ここで、`α` と `β` は実数スカラーで、`A` は対称周期行列であり、積 `B'*C` は対称であることが知られています。すべての行列引数は定数行列である可能性もあります。

*注:* この関数は、`PeriodicArray`、`PeriodicMatrix`、`PeriodicFunctionMatrix` および `HarmonicArray` のタイプの周期行列に対してのみ利用可能です。

```
excitations(swt::SpinWaveTheory, q)
excitations(swt::SpinWaveTheorySpiral, q; branch)
```

ペア `(energies, T)` を返し、励起エネルギーと固有ベクトルを提供します。パフォーマンスのために、行列の割り当てを避ける [`excitations!`](@ref) を使用することをお勧めします。詳細については、[`excitations!`](@ref) のドキュメントを参照してください。

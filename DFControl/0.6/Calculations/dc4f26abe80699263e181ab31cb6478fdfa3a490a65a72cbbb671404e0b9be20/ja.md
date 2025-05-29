```
set_kpoints!(calculation::Calculation{QE}, k_grid::NTuple{3, Int}; print=true)
set_kpoints!(calculation::Calculation{QE}, k_grid::NTuple{6, Int}; print=true)
set_kpoints!(calculation::Calculation{QE}, k_grid::Vector{<:NTuple{4}}; print=true, k_option=:crystal_b)
```

`calculation`の`:k_points`データブロックを設定するための便利な関数です。3つの異なるメソッドは、それぞれ`nscf`、`scf`または`vcrelax`、および`bands`計算を対象としています。`nscf`バージョンでは、`k_points`の明示的なリストが生成されます。

```
set_kpoints!(calculation::Calculation{Wannier90}, k_grid::NTuple{3, Int})
```

`nscf`を対象とした関数と似ており、`k_points`の明示的なリストを生成します。これは`nscf`と同じルールに従います。`mp_grid`フラグも自動的に設定されます。

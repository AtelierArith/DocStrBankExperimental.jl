```
HamiltonianKGrid(hami::TBHamiltonian{T}, nk, H_function_k::Function = x -> nothing) where T
HamiltonianKGrid(hami::TBHamiltonian{T}, k_grid, H_function_k::Function = x -> nothing) where T
```

kグリッドを取り、各kに対してHkを計算し、対角化します。Hkの固有ベクトルと固有値のみが保存され、`H_function_k`関数は中間のHkに対して呼び出されます。
